---
title: "MacBook Air 3,2 Kernel 3.3.6 wifi"
date: 2012-05-22
forum: Apple Hardware Users
---

### Post by whalogreg on 2012-05-22
I updated to the 3.3.6 kernel to fix a display bug with my Air. Unfortunately when I try to activate the wireless driver I get an error, which tells me to look at /var/log/jockey.log which contains this...



```
 2012-05-22 20:04:03,375 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8>
2012-05-22 20:04:06,096 DEBUG: reading modalias file /lib/modules/3.3.6-030306-generic/modules.alias
2012-05-22 20:04:06,228 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-05-22 20:04:06,229 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-05-22 20:04:06,282 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-05-22 20:04:06,290 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-05-22 20:04:06,295 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-05-22 20:04:06,368 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-05-22 20:04:06,368 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-05-22 20:04:06,377 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-05-22 20:04:06,382 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-05-22 20:04:06,383 DEBUG: nvidia.available: falling back to default
2012-05-22 20:04:06,401 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-22 20:04:06,401 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-22 20:04:06,405 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-05-22 20:04:06,411 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-05-22 20:04:06,411 DEBUG: nvidia.available: falling back to default
2012-05-22 20:04:06,445 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-05-22 20:04:06,449 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-22 20:04:06,454 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-05-22 20:04:06,455 DEBUG: nvidia.available: falling back to default
2012-05-22 20:04:06,490 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-22 20:04:06,494 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-05-22 20:04:06,499 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-05-22 20:04:06,499 DEBUG: nvidia.available: falling back to default
2012-05-22 20:04:06,514 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-22 20:04:06,515 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-22 20:04:06,519 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-05-22 20:04:06,524 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-05-22 20:04:06,525 DEBUG: nvidia.available: falling back to default
2012-05-22 20:04:06,541 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-22 20:04:06,541 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-22 20:04:06,546 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-05-22 20:04:06,551 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-05-22 20:04:06,551 DEBUG: nvidia.available: falling back to default
2012-05-22 20:04:06,567 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-22 20:04:06,568 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-22 20:04:06,568 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-05-22 20:04:06,573 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-05-22 20:04:06,573 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-05-22 20:04:06,589 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-05-22 20:04:06,589 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-05-22 20:04:06,594 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-22 20:04:06,612 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-05-22 20:04:06,613 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-05-22 20:04:06,613 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-05-22 20:04:06,635 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-05-22 20:04:06,635 DEBUG: Firmware for DVB cards not available
2012-05-22 20:04:06,635 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-05-22 20:04:06,654 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-05-22 20:04:06,663 DEBUG: Software modem not available
2012-05-22 20:04:06,664 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-05-22 20:04:06,669 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-05-22 20:04:06,670 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-05-22 20:04:06,670 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-05-22 20:04:06,670 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-05-22 20:04:06,676 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-22 20:04:06,681 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-05-22 20:04:06,682 DEBUG: fglrx.available: falling back to default
2012-05-22 20:04:06,714 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-22 20:04:06,719 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-05-22 20:04:06,723 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-05-22 20:04:06,723 DEBUG: fglrx.available: falling back to default
2012-05-22 20:04:06,754 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-05-22 20:04:06,754 DEBUG: all custom handlers loaded
2012-05-22 20:04:06,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-22 20:04:06,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'input:b0003v05ACp023Fe0001-e0,1,3,k110,145,14A,14D,14E,14F,ra0,1,18,1C,30,31,32,33,34,35,36,mlsfw')
2012-05-22 20:04:06,760 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-22 20:04:06,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:06,849 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-22 20:04:06,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:06,850 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-22 20:04:06,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:06,850 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-22 20:04:06,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:06,850 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-22 20:04:06,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:06,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-22 20:04:06,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:APP0001:SMC-MCP:')
2012-05-22 20:04:06,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D6Dsv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'platform:applesmc')
2012-05-22 20:04:07,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D80sv0000106Bsd0000CB89bc06sc01i00')
2012-05-22 20:04:07,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp850Ad0626dcEFdsc02dp01ic0Eisc01ip00')
2012-05-22 20:04:07,184 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-05-22 20:04:07,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-22 20:04:07,185 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-22 20:04:07,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,185 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-22 20:04:07,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp821Bd0034dcFFdsc01dp01icFEisc01ip01')
2012-05-22 20:04:07,186 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-22 20:04:07,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp821Bd0034dcFFdsc01dp01icFFiscFFipFF')
2012-05-22 20:04:07,186 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-22 20:04:07,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2012-05-22 20:04:07,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-22 20:04:07,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'platform:regulatory')
2012-05-22 20:04:07,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D60sv00000000sd00000000bc06sc00i00')
2012-05-22 20:04:07,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D72sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-22 20:04:07,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-22 20:04:07,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D68sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D71sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-22 20:04:07,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D75sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D9Dsv000010DEsd0000CB89bc0Csc03i20')
2012-05-22 20:04:07,206 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd000008A3sv0000106Bsd000000D3bc03sc00i00')
2012-05-22 20:04:07,209 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-05-22 20:04:07,210 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,210 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-05-22 20:04:07,210 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,210 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp023Fd0107dc00dsc00dp00ic03isc01ip02')
2012-05-22 20:04:07,210 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcm5974'}
2012-05-22 20:04:07,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcm5974', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,211 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-22 20:04:07,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,211 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-05-22 20:04:07,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp821Bd0034dcFFdsc01dp01icE0isc01ip01')
2012-05-22 20:04:07,212 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-22 20:04:07,212 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-22 20:04:07,212 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-22 20:04:07,212 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-22 20:04:07,212 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-22 20:04:07,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'input:b0003v05ACp023Fe0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,A8,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,D0,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2012-05-22 20:04:07,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-22 20:04:07,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-22 20:04:07,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:APP0002:BACKLIGHT:')
2012-05-22 20:04:07,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D7Asv000010DEsd0000CB89bc0Bsc40i00')
2012-05-22 20:04:07,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-05-22 20:04:07,217 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-22 20:04:07,217 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,217 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-22 20:04:07,217 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMBA31.88Z.0061.B07.1201241641:bd01/24/12:svnAppleInc.:pnMacBookAir3,2:pvr1.0:rvnAppleInc.:rnMac-942C5DF58193131B:rvrMacBookAir3,2:cvnAppleInc.:ct10:cvrMac-942C5DF58193131B:')
2012-05-22 20:04:07,235 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000014E4d00004353sv0000106Bsd000000D1bc02sc80i00')
2012-05-22 20:04:07,283 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-05-22 20:04:07,284 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:07,283 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-05-22 20:04:07,287 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-22 20:04:07,288 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:07,288 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-05-22 20:04:07,288 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-05-22 20:04:07,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-22 20:04:07,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v13B1p0020d0001dc00dsc00dp00icFFiscFFipFF')
2012-05-22 20:04:07,297 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb'}
2012-05-22 20:04:07,297 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D94sv000010DEsd0000CB89bc04sc03i00')
2012-05-22 20:04:07,301 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-22 20:04:07,301 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp850Ad0626dcEFdsc02dp01icFFisc00ip00')
2012-05-22 20:04:07,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D7Bsv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp821Bd0034dcFFdsc01dp01icFFisc01ip01')
2012-05-22 20:04:07,306 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-22 20:04:07,306 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v1D6Bp0001d0303dc09dsc00dp00ic09isc00ip00')
2012-05-22 20:04:07,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp023Fd0107dc00dsc00dp00ic03isc01ip01')
2012-05-22 20:04:07,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-22 20:04:07,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-05-22 20:04:07,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D6Fsv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D76sv000010DEsd00000000bc06sc04i00')
2012-05-22 20:04:07,313 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-05-22 20:04:07,314 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'input:b0003v05ACp850Ae0626-e0,1,kD4,ramlsfw')
2012-05-22 20:04:07,314 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-22 20:04:07,314 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,314 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-22 20:04:07,314 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D6Esv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v1D6Bp0002d0303dc09dsc00dp00ic09isc00ip00')
2012-05-22 20:04:07,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-22 20:04:07,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-05-22 20:04:07,320 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-05-22 20:04:07,320 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-22 20:04:07,320 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,320 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:MIKEY:')
2012-05-22 20:04:07,320 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp023Fd0107dc00dsc00dp00ic03isc00ip00')
2012-05-22 20:04:07,321 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-22 20:04:07,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'platform:pcspkr')
2012-05-22 20:04:07,322 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-05-22 20:04:07,322 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,322 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-05-22 20:04:07,322 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D88sv0000106Bsd0000CB89bc01sc06i01')
2012-05-22 20:04:07,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D70sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D69sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp8403d9833dc00dsc00dp00ic08isc06ip50')
2012-05-22 20:04:07,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-05-22 20:04:07,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'usb:v05ACp850Ad0626dcEFdsc02dp01ic0Eisc02ip00')
2012-05-22 20:04:07,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-05-22 20:04:07,333 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-22 20:04:07,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,333 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-22 20:04:07,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-22 20:04:07,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'pci:v000010DEd00000D79sv000010DEsd0000CB89bc0Csc05i00')
2012-05-22 20:04:07,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cc0fc8> about HardwareID('modalias', 'acpi:SMBUS:')
2012-05-22 20:04:07,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-22 20:04:07,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'input:b0003v05ACp023Fe0001-e0,1,3,k110,145,14A,14D,14E,14F,ra0,1,18,1C,30,31,32,33,34,35,36,mlsfw')
2012-05-22 20:04:07,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:APP0001:SMC-MCP:')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D6Dsv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'platform:applesmc')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D80sv0000106Bsd0000CB89bc06sc01i00')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp850Ad0626dcEFdsc02dp01ic0Eisc01ip00')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp821Bd0034dcFFdsc01dp01icFEisc01ip01')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp821Bd0034dcFFdsc01dp01icFFiscFFipFF')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-22 20:04:07,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'platform:regulatory')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D60sv00000000sd00000000bc06sc00i00')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D72sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D68sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D71sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D75sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D9Dsv000010DEsd0000CB89bc0Csc03i20')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd000008A3sv0000106Bsd000000D3bc03sc00i00')
2012-05-22 20:04:07,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp023Fd0107dc00dsc00dp00ic03isc01ip02')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp821Bd0034dcFFdsc01dp01icE0isc01ip01')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'input:b0003v05ACp023Fe0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,A8,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,D0,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:APP0002:BACKLIGHT:')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D7Asv000010DEsd0000CB89bc0Bsc40i00')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMBA31.88Z.0061.B07.1201241641:bd01/24/12:svnAppleInc.:pnMacBookAir3,2:pvr1.0:rvnAppleInc.:rnMac-942C5DF58193131B:rvrMacBookAir3,2:cvnAppleInc.:ct10:cvrMac-942C5DF58193131B:')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000014E4d00004353sv0000106Bsd000000D1bc02sc80i00')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v13B1p0020d0001dc00dsc00dp00icFFiscFFipFF')
2012-05-22 20:04:07,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D94sv000010DEsd0000CB89bc04sc03i00')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp850Ad0626dcEFdsc02dp01icFFisc00ip00')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D7Bsv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp821Bd0034dcFFdsc01dp01icFFisc01ip01')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v1D6Bp0001d0303dc09dsc00dp00ic09isc00ip00')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp023Fd0107dc00dsc00dp00ic03isc01ip01')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D6Fsv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D76sv000010DEsd00000000bc06sc04i00')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'input:b0003v05ACp850Ae0626-e0,1,kD4,ramlsfw')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D6Esv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v1D6Bp0002d0303dc09dsc00dp00ic09isc00ip00')
2012-05-22 20:04:07,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:MIKEY:')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp023Fd0107dc00dsc00dp00ic03isc00ip00')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'platform:pcspkr')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D88sv0000106Bsd0000CB89bc01sc06i01')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D70sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D69sv00000000sd00000000bc05sc00i00')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp8403d9833dc00dsc00dp00ic08isc06ip50')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'usb:v05ACp850Ad0626dcEFdsc02dp01ic0Eisc02ip00')
2012-05-22 20:04:07,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-05-22 20:04:07,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'pci:v000010DEd00000D79sv000010DEsd0000CB89bc0Csc05i00')
2012-05-22 20:04:07,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3035f80> about HardwareID('modalias', 'acpi:SMBUS:')
2012-05-22 20:04:07,370 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:07,401 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:07,420 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:10,674 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:17,792 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-22 20:04:17,793 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-05-22 20:04:17,847 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:18,140 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-22 20:04:18,141 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-05-22 20:04:18,213 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:28,895 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:28,917 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:28,936 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:28,946 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:31,532 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:31,556 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-22 20:04:31,575 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

Any ideas?

---

### Post by pbhedlund on 2012-05-23
See my response in your other thread ([http://ubuntuforums.org/showpost.php?p=11961814&postcount=4](http://ubuntuforums.org/showpost.php?p=11961814&postcount=4)).

---

