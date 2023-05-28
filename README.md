# Hackintosh-EFI-ThinkPadT540p
## Lenovo ThinkPad T540p，Black Apple，EFI

### Software Version
| Software | Version |
| --- | :--: |
| System | macOS Big Sur 11.6.5 (20G527) |
| Bootloader | OpenCore v0.8.0 |

### My Hardware Setup
|   Hardware    |   Model  |
| -------- | :----: |
| Laptop | Lenovo ThinkPad T540p |
| CPU | Intel Core I5-4300M |
| RAM | 6GB (4gb+2gb) DDR3L 1600MHz |
| HDD | Kingston SSD 500GB |
| GPU | Intel HD Graphics 4600 |
| Display | 1080p FHD 15.6 |
| Wifi adapter | Intel 7260AC |

## BIOS SETTINGS 

Note: This Bios Setup is from [This Repo](https://github.com/VinylNerd/ThinkPad-T440P-OpenCore/blob/main/README.md)

The BIOS must be properly configured prior to installing macOS.

In Security menu, set the following settings:

    Security > Security Chip: must be Disabled,
    Memory Protection > Execution Prevention: must be Enabled,
    Internal Device Access > Bottom Cover Tamper Detection: must be Disabled,
    Anti-Theft > Current Setting: must be Disabled,
    Anti-Theft > Computrace > Current Setting: must be Disabled,
    Secure Boot > Secure Boot: must be Disabled.

In Startup menu, set the following options:

    UEFI/Legacy Boot: Both,
    UEFI/Legacy Priority: UEFI First,
    CSM Support: Yes. VERY IMPORTANT!!!

Now you can go through the install.

### Completeness
+ Normal drive of nuclear display, 2048MB video memory
+ normal sound card driver
+ The Wi-Fi works normally, but the Bluetooth is unstable (the Bluetooth connection is normal, the sound is not stuttered; the connection to the Logitech AnyWhere3 Bluetooth mouse fails), and the airdrop cannot be used.
+ USB customization, all USB ports are normal
+ SD card reader drives normally
+ M.2 (Sata) hard disk installed with Win10, OC can boot Win10
+ The boot interface is graphical, and there is a "duang" sound when booting

### Defect
+ Sleep blurred screen, disable sleep, hibernation (Forward the original address of the CSDN tutorial：[Black Apple completely disable sleep](https://blog.csdn.net/fjh1997/article/details/112559539)）
```bash
# Before doing anything, save your current configuration using
pmset -g
# To disable sleep 彻底禁用
sudo pmset -a sleep 0; sudo pmset -a hibernatemode 0; sudo pmset -a disablesleep 1;
# And to go back to normal 还原
sudo pmset -a sleep 1; sudo pmset -a hibernatemode [original hibernatemode value]; sudo pmset -a disablesleep 0;
```
+ Intel network card, bluetooth is unstable (bluetooth connection is normal, sound is not stuttering; connection to Logitech AnyWhere3 bluetooth mouse fails), and airdrop cannot be used

### Remark
1. For the model selection of PlatformInfo, "MacBookPro11,1" must be selected, otherwise the boot card progress bar
2. The core display buffer frame patch of DeviceProperties, PciRoot(0x0)/Pci(0x2,0x0), AAPL, ig-platform-id is 0300220D, device-id is 12040000. Although it seems that it does not match the current nuclear display model, but replace it with another one, the progress bar of the boot card

### Screenshots
![关于本机.png](https://github.com/demon3434/Hackintosh-EFI-ThinkPadT540p/blob/main/OpenCore%20v0.8.0%20%26%20macOS%20Big%20Sur%2011.6.5%20(20G527)/1.%E5%85%B3%E4%BA%8E%E6%9C%AC%E6%9C%BA.png "关于本机")
![PlatformInfo机型选择.png](https://github.com/demon3434/Hackintosh-EFI-ThinkPadT540p/blob/main/OpenCore%20v0.8.0%20%26%20macOS%20Big%20Sur%2011.6.5%20(20G527)/2.OCC%E6%9C%BA%E5%9E%8B%E9%80%89%E6%8B%A9.png "PlatformInfo机型选择")
![核显缓冲帧补丁.png](https://github.com/demon3434/Hackintosh-EFI-ThinkPadT540p/blob/main/OpenCore%20v0.8.0%20%26%20macOS%20Big%20Sur%2011.6.5%20(20G527)/3.%E6%A0%B8%E6%98%BE%E7%BC%93%E5%86%B2%E5%B8%A7%E8%A1%A5%E4%B8%81.png "核显缓冲帧补丁")
![Hackintool系统信息.png](https://github.com/demon3434/Hackintosh-EFI-ThinkPadT540p/blob/main/OpenCore%20v0.8.0%20%26%20macOS%20Big%20Sur%2011.6.5%20(20G527)/4.Hackintool%E7%B3%BB%E7%BB%9F%E4%BF%A1%E6%81%AF.png "Hackintool系统信息")
