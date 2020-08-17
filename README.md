# MSI-Z170iProGamingAC-Hackintosh-Clover
This tutorial works perfectly on macOS Catalina (10.15.5). FCPX GPU rendering works smoothly. HDR can be enabled. Supports sleep, Airdrop and Handoff. 

![image](Screenshot_en-us.png)


## Hardware
| Item | Brand | Model | Driver | Comment |
|-----|-----|-----|-----|-----|
| Motherboard | MSI | Z170i Gaming Pro AC | | |
| CPU | Intel | i5-6600K | | |
| RAM | KLEVV | BOLT 2x8GB DDR4 3200 | | Overclocked to 4000 |
| iGPU | Intel | HD Graphics 530 | built-in | Headless mode |
| dGPU | Sapphire | RX 470 Reference Edition 4GB | | |
| SSD | ADATA | SX6000Pro 512GB NVMe | Built-In | |
| Wireless | Broadcom | BCM94360NG M.2 | built-in | QCA61x4A was replaced* |
| Ethernet | Intel | I219-V | [IntelMausi.kext](https://github.com/acidanthera/IntelMausi) | |
| Audio | Realtek | ALC1150 | [AppleALC.kext](https://github.com/acidanthera/AppleALC) | |
| PSU | Enermax | 450W 80+ Bronze | | |
| Case | Silverstone | Mini-ITX | | |
| Monitor | HP | 24f (FreeSync) | | |

*QCA61x4A is not supported. Follow [this guide](https://www.tonymacx86.com/threads/bcm94352z-installed-on-asus-z170i-pro-gaming-wifi-and-bt.191274) the replace the onboard wireless card. Theoretically BCM94352Z or BCM94360CS2 with adapter can work as well.
## BIOS Setup
| Name | Option |
| --- | --- |
| SW Guard Extensions (SGX) | Disabled |
| CFG Lock | Disabled |
| VT-d | Disabled |
| Above 4G Decoding | Enabled |
| Primary Display | PCIE |
| iGPU-Multi-Monitor | Enabled |
| DVMT Pre-Allocated | 128M |
| IOAPIC 24-119 Entries | Disabled |
| Network Stack | Disabled |
| Legacy USB Support| Enabled |
| Fast Boot | Disabled |
| OS Type | Other OS |
| Launch CSM | Disabled |

## Installation
### Pre Installation
Download the official macOS Catalina image, [Clover Configurator](https://mackie100projects.altervista.org/download-clover-configurator/) and [Hackintool](https://github.com/headkaze/Hackintool).

**DO NOT** use UniBeast to create the drive. It may create strange errors. And do not use MultiBeast for post installation jobs.

Follow [this guide](https://hackintosher.com/guides/how-to-make-a-macos-10-15-catalina-flash-drive-installer/) to create the boot drive. Copy my `/EFI` folder into the EFI partition of your boot drive. Also copy Clover Configurator and Hackintool into the main partition.

### During Installation 
Press F11 to boot into your flash drive. Move to **Boot macOS Install from Install macOS Catalina** and press spacebar to add -v(verbose) to display debug messages. If USB 3.0 gives error, switch to **USB 2.0**.

Before installation, first open **Disk Utility** to erase the drive. You can choose either APFS(recommended) or HFS+ with GUID partition map.

The system will auto reboot from USB for several times. In initialization page **DO NOT** connect to internet and login iCloud, Create a local account instead. Then you should be able to reach the desktop.

### Post Installation
After the first boot, open Clover Configurator to mount both EFI partitions in SSD and flash drive.

Copy everything from the EFI in flash drive to the EFI in SSD and reboot. Now you should be able to boot from SSD.

Refer to [this guide](https://hackintosher.com/forums/thread/generate-your-own-hackintosh-serial-number-board-serial-number-uuid-mlb-rom-in-clover.306) to generate serial number. Save and reboot. Then you should be able to login iCloud.

Enjoy your own Hackintosh!

## Comments
1. If your iGPU is not HD 530, refer to [this guide](https://www.tonymacx86.com/threads/an-idiots-guide-to-lilu-and-its-plug-ins.260063/#Headless) to recongnize the model correctly.
2. If you don't have a dGPU, i.e. output via iGPU, refer to [this guide](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/config.plist-per-hardware/skylake#properties) to modify `/EFI/CLOVER/config.plist`.
3. If your motherboard is not MSI Z170i Gaming Pro AC, refer to [this guide](https://www.tonymacx86.com/threads/the-new-beginners-guide-to-usb-port-configuration.286553) to create your own USB patch.

## Known issue
GPU fan spins at max RPM for several seconds during boot occasionally and runs normally in desktop. This might be a BIOS bug. You may choose any other Polaris GPUs.

## USB Map 
HS01 HS02 HS07 HS08 HS09 HS10 HS11 HS12 SS01 SS02 SS03 SS04 SS05 SS06 SS10
