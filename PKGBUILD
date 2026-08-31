# Maintainer: Jon <jon@example.com>
pkgname=lumabri
pkgver=0.1.0
pkgrel=5
pkgdesc='Peer-to-peer distributed inference and model serving for Colibri'
arch=('x86_64')
url='https://github.com/JustVugg/lumabri'
license=('Apache-2.0')
depends=('gcc-libs' 'glibc' 'libgomp' 'python')
makedepends=('make' 'gcc')
provides=('lumabri')
conflicts=('lumabri-git')
source=()
sha256sums=()

build() {
  cd "$startdir"
  make -B ENGINE="${COLIBRI_ENGINE_DIR:-$startdir/../colibri/c}" all
}

package() {
  cd "$startdir"
  for binary in lumabri tracker maintainer segment_node segment_chat; do
    install -Dm755 "$binary" "$pkgdir/usr/bin/$binary"
  done
  install -Dm755 openai_proxy.py "$pkgdir/usr/bin/lumabri-openai-proxy"
  install -Dm755 liblumabri.so "$pkgdir/usr/lib/lumabri/liblumabri.so"
  install -Dm644 README.md "$pkgdir/usr/share/doc/$pkgname/README.md"
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
