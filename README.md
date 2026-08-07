# Droidspaces kernel for Oneplus 9 crDroid

这两个补丁用于修复 GKI 内核的 ABI 兼容性问题，让你可以在不破坏内核 ABI 的前提下启用特定内核功能。

## 补丁列表

| 补丁文件 | 功能 |
|---------|------|
| 001.GKI-below-6.12-fix_sysvipc_kabi_1_2_3.patch | 为 SYSVIPC 添加 ABI padding |
| 002.5.10_or_lower_use_android_abi_padding_for_posix_mqueue.patch | 为 POSIX_MQUEUE 添加 ABI padding|

## 使用方法

克隆上游内核源码：

```bash
git clone https://github.com/crdroidandroid/android_kernel_oneplus_sm8350
cd android_kernel_oneplus_sm8350
```

下载并应用补丁：

```bash
wget https://raw.githubusercontent.com/quilluna/android_kernel_oneplus_sm8350_ds/master/001.GKI-below-6.12-fix_sysvipc_kabi_1_2_3.patch
wget https://raw.githubusercontent.com/quilluna/android_kernel_oneplus_sm8350_ds/master/002.5.10_or_lower_use_android_abi_padding_for_posix_mqueue.patch
git apply 001.GKI-below-6.12-fix_sysvipc_kabi_1_2_3.patch
git apply 002.5.10_or_lower_use_android_abi_padding_for_posix_mqueue.patch
```

开始编译（建议使用官方编译器），编译完成后使用 AnyKernel3 打包内核并刷入即可

此外，也可以 Fork 本仓库，使用 Github Action 自动构建。

## 补丁详情

**001 - SYSVIPC KABI Padding**

此补丁从 [Droidspaces OSS 仓库](https://github.com/ravindu644/Droidspaces-OSS/tree/main/Documentation/resources/kernel-patches/GKI/below-kernel-6.12) 获取，文件名为 `001.GKI-below-6.12-fix_sysvipc_kabi_1_2_3.patch` 无修改


**002 - POSIX_MQUEUE KABI Padding**

此补丁从 [Droidspaces OSS 仓库](https://github.com/ravindu644/Droidspaces-OSS/tree/main/Documentation/resources/kernel-patches/GKI/below-kernel-6.12) 获取，文件名为`002.5.10_or_lower_use_android_abi_padding_for_posix_mqueue.patch`，去除`ANDROID_OEM_DATA_ARRAY(1, 2)`宏，确保结构体一致。


## 致谢 (排名不分先后)

- [Droidspaces](https://github.com/ravindu644/Droidspaces-OSS) — powerful Android container tool
- [KernelSU Next](https://github.com/KernelSU-Next/KernelSU-Next) — kernel-level root
- [Neutron Clang](https://github.com/Neutron-Toolchains/clang-build-catalogue) — default toolchain
- [crDroid Android](https://crdroid.net/) — ROM source
- [crDroid Android Kernel SM8350](https://github.com/crdroidandroid/android_kernel_oneplus_sm8350) — kernel source base
- [osm0sis](https://github.com/osm0sis) — AnyKernel3 author

## License

与 Linux 内核保持一致，采用 GPL v2。
