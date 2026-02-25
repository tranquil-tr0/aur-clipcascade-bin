# Maintainer: Seunghun Kim <seunghunkim at proton dot me>
pkgname=clipcascade-bin
pkgver=3.1.0
pkgrel=5
pkgdesc="ClipCascade: Sync clipboard across multiple devices"
arch=('x86_64')
url="https://github.com/Sathvik-Rao/ClipCascade"
license=('GPL-3.0')
depends=(
    'tk'
    'python'
    'python-pillow'
    'python-plyer'
    'python-pycryptodome'
    'python-pystray'
    'python-requests'
    'python-websocket-client'
    'python-xxhash'
    'python-pyfiglet'
    'python-beautifulsoup4'
    'python-aiortc'
    'python-ifaddr'
    'python-pywayland'
)
optdepends=('xclip: Xorg X Display Server support'
            'wl-clipboard: Wayland Display Server support')
makedepends=('unzip')
source=(
    "ClipCascade_Linux.zip::https://github.com/tranquil-tr0/ClipCascade/releases/download/1/rel.zip"
    "clipcascade.png::https://raw.githubusercontent.com/Sathvik-Rao/ClipCascade/refs/tags/3.0.0/logo/logo.png"
    "clipcascade.desktop"
)
sha256sums=(
    'b56f22b21ff57ca63c0b29976e2066724e0d3f59eb5c180625544dc8d986edd9'
    '54974fabd99d918ea142163db566a98d3ca1a43b5a0f3d0c7ed7224ecccbd3b9'
    '6b90177c1c1ed1e575cb1f553cd2cde4b2b92d32743e32ec046aaf2ed3674594'
)

prepare() {
    unzip -o "${srcdir}/ClipCascade_Linux.zip" -d "${srcdir}/ClipCascade"
}

package() {
    install -d "${pkgdir}/usr/share/clipcascade"
    cp -r "${srcdir}/ClipCascade-linux-release/"* "${pkgdir}/usr/share/clipcascade/"

    install -d "${pkgdir}/usr/bin"
    install -Dm755 /dev/stdin "${pkgdir}/usr/bin/clipcascade" << EOF
#!/bin/sh
exec python /usr/share/clipcascade/main.py "\$@"
EOF

    install -Dm644 "${srcdir}/ClipCascade-linux-release/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    install -Dm644 "${srcdir}/clipcascade.desktop" "${pkgdir}/usr/share/applications/clipcascade.desktop"
    install -Dm644 "${srcdir}/clipcascade.png" "${pkgdir}/usr/share/pixmaps/clipcascade.png"
}
