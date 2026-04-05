# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as
#    published by the Free Software Foundation, either version 3 of the
#    License, or (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public
#    License along with this program.
#    If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributors:
#   Thomas Bächler
#     <thomas@archlinux.org>
#   Gaetan Bisson
#     <bisson@archlinux.org>
#   Jelle van der Waa
#     <jelle@archlinux.org>

_os="$(
  uname \
    -o)"
_evmfs_available="$(
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
if [[ ! -v "_git" ]]; then
  _git="true"
fi
if [[ ! -v "_offline" ]]; then
  _offline="false"
fi
if [[ ! -v "_git_service" ]]; then
  _git_service="github"
fi
if [[ ! -v "_archive_format" ]]; then
  if [[ "${_git}" == "true" ]]; then
    if [[ "${_evmfs}" == "true" ]]; then
      _archive_format="bundle"
    elif [[ "${_evmfs}" == "false" ]]; then
      _archive_format="git"
    fi
  elif [[ "${_git}" == "false" ]]; then
    if [[ "${_git_service}" == "github" ]]; then
      _archive_format="zip"
    elif [[ "${_git_service}" == "gitlab" ]]; then
      _archive_format="tar.gz"
    fi
  fi
fi
_pkg=iana-etc
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
_commit="45b16530eb92c9ef628787234d90b3c06a43bf37"
pkgver=20260328
_ports=service-names-port-numbers-${pkgver}
_protocols=protocol-numbers-20260310
pkgrel=9
_pkgdesc=(
  "/etc/protocols and /etc/services"
  "provided by IANA."
)
pkgdesc="${_pkgdesc[*]}"
url="https://www.iana.org/protocols"
arch=(
  'any'
)
license=(
  'custom:none'
)
backup=(
  'etc/'{"protocols","services"}
)
makedepends=()
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    "git"
  )
fi
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
fi
_http="https://sources.archlinux.org"
_ns="other/packages"
sha256sums=()
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
_tarfile="${_tarname}.${_archive_format}"
source=()
sha256sums=()
_bundle_sum="f66aea2c9bd20bcd827ce58e9176b4bac78ab2489b72b07ea4b6b5dc33dee54f"
_bundle_sig_sum="b09b2b555d2e4ffe41865420f88931257f0b070b13c1699525a962cea64ab305"
_ports_sum='05dcb6075f7b06abb876f645c9f778653b558566f28b336d3f42374e3ababbaf'
_protocols_sum='59cdd7930cd6152bd11713b8883503511fffb2add72345d21d043cecb969803b'
_sum="${_bundle_sum}"
_sig_sum="${_bundle_sig_sum}"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_sig_sum}"
_sig_src="${_tarfile}.sig::${_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_git}" == "false" ]]; then
    _msg=(
      "ahah, funny"
    )
    echo \
      "${_msg[*]}" \
      1>&2
    exit \
      1
  elif [[ "${_git}" == "true" ]]; then
    _src="${_evmfs_src}"
    _sum="${_bundle_sum}"
    source+=(
      "${_sig_src}"
    )
    sha256sums+=(
      "${_bundle_sig_sum}"
    )
  fi
elif [[ "${_evmfs}" == "false" ]]; then
  _ports_src="${_http}/${_ns}/${_pkg}/${_ports}.xml"
  _protocols_src="${_http}/${_ns}/${_pkg}/${_protocols}.xml"
  source+=(
    "${_ports_src}"
    "${_protocols_src}"
  )
  sha256sums+=(
    "${_ports_sum}"
    "${_protocols_sum}"
  )
fi
source+=(
  'license-from-upstream'
)
sha256sums+=(
  'dd37e92942d5a4024f1c77df49d61ca77fc6284691814903a741785df61f78cb'
)
validpgpkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

# Original but unversioned IANA files:
# https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xml
# https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xml

_git_unbundle() {
  local \
    _tarname="${1}" \
    _bundle \
    _repo \
    _msg=()
  _bundle="${srcdir}/${_tarname}.bundle"
  _repo="${srcdir}/${_tarname}"
  _msg=(
    "Cloning '${_bundle}' into '${_repo}'."
  )
  msg \
    "${_msg[*]}"
  git \
    clone \
      "${_bundle}" \
      "${_repo}" || \
  git \
    -C \
      "${_repo}" \
      pull || \
  true
}

_git_unbundle_update() {
  local \
    _repo="${1}" \
    _bundle="${2}" \
    _repo \
    _msg=()
  _bundle_name="$(
    basename \
      "${_bundle}")"
  _msg=(
    "Updating '${_repo}' from '${_bundle}'."
  )
  msg \
    "${_msg[*]}"
  git \
    -C \
      "${_repo}" \
      remote \
        add \
          "${_bundle_name}" \
          "${_bundle}" ||
  true
  git \
    -C \
      "${_repo}" \
    pull \
      "${_bundle_name}" || \
  true
}

prepare() {
  local \
    _commit_hash
  if [[ "${_evmfs}" == "true" ]]; then
    if [[ "${_git}" == "false" ]]; then
      ur \
        "${_like}"
    elif [[ "${_git}" == "true" ]]; then
      _git_unbundle \
        "${_tarname}"
      # If there will be need to update this
      # before evm-git / evmfs 1.0 release
      # _git_unbundle_update \
      #   "${srcdir}/${_tarname}" \
      #   "${srcdir}/${_pkg}-${_commit_next}"
    fi
  fi
}



package() {
  cd \
    "${srcdir}"
  install \
    -vdm755 \
    "${pkgdir}/etc"
  install \
    -vDm644 \
    "license-from-upstream" \
    "${pkgdir}/usr/share/licenses/iana-etc/LICENSE"
  install \
    -vDm644 \
    "${_ports}.xml" \
    "${pkgdir}/usr/share/iana-etc/port-numbers.iana"
  install \
    -vDm644 \
    "${_protocols}.xml" \
    "${pkgdir}/usr/share/iana-etc/protocol-numbers.iana"
  
  gawk \
    -F \
      "[<>]" \
    '
BEGIN { print "# Full data: /usr/share/iana-etc/protocol-numbers.iana\n" }
(/<record/) { v=n="" }
(/<value/) { v=$3 }
(/<name/ && $3!~/ /) { n=$3 }
(/<\/record/ && n && v!="") { printf "%-12s %3i %s\n", tolower(n),v,n }
' \
    "${_protocols}.xml" > \
    "${pkgdir}/etc/protocols"
  gawk \
    -F \
      "[<>]" \
    '
BEGIN { print "# Full data: /usr/share/iana-etc/port-numbers.iana\n" }
(/<record/) { n=u=p=c="" }
(/<name/ && !/\(/) { n=$3 }
(/<number/) { u=$3 }
(/<protocol/) { p=$3 }
(/Unassigned/ || /Reserved/ || /historic/) { c=1 }
(/<\/record/ && n && u && p && !c) { printf "%-15s %5i/%s\n", n,u,p }
' \
    "${_ports}.xml" > \
    "${pkgdir}/etc/services"
}
