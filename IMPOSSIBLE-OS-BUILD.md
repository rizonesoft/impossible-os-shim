# Building shimx64.efi for Impossible OS

This is the rhboot/shim fork used by Impossible OS. Our vendor certificate
(`vendor-cert/MOK.cer`) is embedded so the shim trusts our signed bootloader.

## Build (Docker — matches shim-review submission)

```bash
docker build -t impossible-os-shim .  # requires Dockerfile from rizonesoft/shim-review
docker run --rm impossible-os-shim sha256sum /output/shimx64.efi
# Expected: d7e21770b1c8f2b977db1d533f7bba3d0de3d212e83ffd35c2509de970d6bd2f
```

## Manual Build

```bash
make VENDOR_CERT_FILE=vendor-cert/MOK.cer ARCH=x86_64 shimx64.efi mmx64.efi
```

## SHA256 (built binaries)

```
d7e21770b1c8f2b977db1d533f7bba3d0de3d212e83ffd35c2509de970d6bd2f  shimx64.efi
0141578fa3270f55afd0639a91f1d56edb1f5bec5be2462e8b2edf9918ec1248  mmx64.efi
```
