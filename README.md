# Hackintosh Fujitsu LIFEBOOK UH90/B1
Hackintosh for [Fujitsu LIFEBOOK UH90/B1 (UH Series)](https://www.fmworld.net/fmv/uh/1701/spec/)

![OpenCore version](https://img.shields.io/badge/OpenCore-1.0.7-blue?style=flat-square&logo=circle) ![macOS version](https://img.shields.io/badge/macOS-Ventura-green?style=flat-square&logo=apple)

## :gear: What's Working

| **Hardware**    | **Detail**                                                | **Status**         |
| --------------- | --------------------------------------------------------- | ------------------ |
| **CPU**         | Intel Core i5-7200U Processor                             | :white_check_mark: |
| **GPU**         | Intel UHD Graphics 620                                    | :white_check_mark: |
| **Display**     | SHP14B0 13.3inch 1920x1080p                               | :white_check_mark: |
|                 | HDMI / Type-C Output                                      | :white_check_mark: |
| **Audio**       | Realtek ALC255 HD Audio                                   | :white_check_mark: |
|                 | 3.5mm AUX Output                                          | :white_check_mark: |
| **Ethernet**    | Intel Ethernet Connection I219-V                          | :white_check_mark: |
| **Wireless**    | Intel Dual Band Wireless-AC 8265                          | :white_check_mark: |
| **Camera**      | Chicony Electronics Co., Ltd FJ/IR Camera                 | :x:                |
| **Keyboard**    | Fujitsu PS/2 Japanese keyboard (106/109 Key)              | :white_check_mark: |
|                 | Brightness Key                                            | :x:                |
| **TouchPad**    | Synaptics SMBus TouchPad                                  | :white_check_mark: |
| **Card Reader** | BayHubTech OZ621/OZ777 MMC/SD Controller                  | :white_check_mark: |
| **Finger Print**|                                                           | :x:                |
| **SMBIOS**      | MacBookPro14,1                                            | :apple:            |

## :hammer_and_wrench: BIOS Settings
### Disable
You can make below options disable via original BIOS. 
- Fast Boot (in Advanced->Boot Configurations)
- Secure Boot (in Security->Secure Boot Configurations)
- Intel(R) PTT (in Advanced->Internal Device Configurations)
- Intel(R) SGX (in Advanced->CPU Configurations)

On the other hand, you need change below BIOS options too via [`setup_var.efi`](https://github.com/datasone/setup_var.efi) in UEFI Shell.

```sh
# CFG Lock 0x1->0x0
setup_var.efi CpuSetup:0x3C=0x00

# Above 4GB MMIO BIOS assignment 0x0->0x1
setup_var.efi SaSetup:0xE4=0x01

# DVMT Pre-Allocated 32mb(0x1)->64mb(0x2)
setup_var.efi SaSetup:0xDF=0x02
```

## :muscle: Usage
1. Generate SMBIOS info and put it into `config.plist`.
2. Mount EFI partition of your bootable disk. (Reference: https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#setting-up-opencore-s-efi-environment)
3. Put your EFI folder into mounted EFI partition.
