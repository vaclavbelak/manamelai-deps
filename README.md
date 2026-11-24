# manamelai-deps

Pinned binary dependencies for building the Manamel iOS app. This is **not** an
official Microsoft or ONNX Runtime channel.

## onnxruntime-1.22.0

The `vad` Flutter plugin needs the CocoaPods `onnxruntime-c` and
`onnxruntime-objc` 1.22.0. Their CocoaPods trunk specs download from
`download.onnxruntime.ai`, which has served a mismatched TLS certificate since
2026-11-21, and the `microsoft/onnxruntime*` GitHub repositories have been
private since 2026-11-17.

The release `onnxruntime-1.22.0` holds unmodified copies of the two pod
archives, as extracted by `pod install` from the upstream host on 2026-11-18
and zipped without further changes:

| File | sha256 |
|---|---|
| `pod-archive-onnxruntime-c-1.22.0.zip` | `7f22c943b8fd3390699f64a4149453394d95747d261492317b18e8b5c2be0ad0` |
| `pod-archive-onnxruntime-objc-1.22.0.zip` | `d173ff3f8aa28851ba262d33681a663c6e0bc5331049629144e603021eda2275` |

These are not Microsoft's original archive bytes, which are no longer
available; there is no published checksum to compare against. Podspecs that
consume them pin the sha256 above.

## Licences

ONNX Runtime is MIT licensed, Copyright (c) Microsoft Corporation. Both zips
contain its `LICENSE`. The release also carries:

- `LICENSE-onnxruntime`: the same MIT text, from the official 1.22.0 wheel.
- `ThirdPartyNotices-onnxruntime-1.22.0.txt`: Microsoft's third-party notices
  for 1.22.0, taken unmodified from `onnxruntime-1.22.0-cp312-cp312-macosx_13_0_universal2.whl`
  on PyPI (wheel sha256 `f3c0380f53c1e72a41b3f4d6af2ccc01df2c17844072233442c3a7e74851ab97`,
  file sha256 `e9e90971a8e75a9a8ac0c6412e29c1202d079998389915aa485f46c816c3b4cc`).
  It covers every ONNX Runtime build; the iOS binaries contain only a subset.

Do not replace release assets in place; a new version is a new release tag.
