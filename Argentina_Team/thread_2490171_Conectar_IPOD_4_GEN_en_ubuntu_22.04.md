---
title: "Conectar IPOD 4 GEN en ubuntu 22.04"
date: 2023-08-24
forum: Argentina Team
---

### Post by pes4mastermilangm on 2023-08-24
tengo problema para leer mi ipod y manejar las canciones , al conectar me da el mensaje que dejo, alguien me podria ayudar con este problema que me tiene loco, gracias

```
Aug 24 16:03:37 luis-7400 kernel: [19851.414290] usb 1-2: new high-speed USB device number 14 using xhci_hcd
Aug 24 16:03:38 luis-7400 kernel: [19851.574091] usb 1-2: New USB device found, idVendor=05ac, idProduct=129e, bcdDevice= 4.10
Aug 24 16:03:38 luis-7400 kernel: [19851.574105] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug 24 16:03:38 luis-7400 kernel: [19851.574110] usb 1-2: Product: iPod
Aug 24 16:03:38 luis-7400 kernel: [19851.574114] usb 1-2: Manufacturer: Apple Inc.
Aug 24 16:03:38 luis-7400 kernel: [19851.574117] usb 1-2: SerialNumber: 49ab28b8ae516f803c55272ea9338a3660484ada
Aug 24 16:03:27 luis-7400 tracker-miner-f[1762]: g_str_has_suffix: assertion 'str != NULL' failed
Aug 24 16:03:38 luis-7400 mtp-probe: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2"
Aug 24 16:03:38 luis-7400 mtp-probe: bus: 1, device: 14 was not an MTP device
Aug 24 16:03:38 luis-7400 usbmuxd[15422]: libusb: warning [op_get_configuration] device unconfigured
Aug 24 16:03:38 luis-7400 usbmuxd[15422]: libusb: error [op_get_active_config_descriptor] device unconfigured
Aug 24 16:03:38 luis-7400 usbmuxd[15422]: [16:03:38.149][3] Could not get old configuration descriptor for device 1-14: LIBUSB_ERROR_NOT_FOUND
Aug 24 16:03:38 luis-7400 kernel: [19852.392348] ipheth 1-2:4.2: Apple iPhone USB Ethernet device attached
Aug 24 16:03:38 luis-7400 usbmuxd[15422]: [16:03:38.938][3] Connecting to new device on location 0x1000e as ID 6
Aug 24 16:03:38 luis-7400 usbmuxd[15422]: [16:03:38.939][3] Connected to v2.0 device 6 on location 0x1000e with serial number 49ab28b8ae516f803c55272ea9338a3660484ada
Aug 24 16:03:38 luis-7400 NetworkManager[642]: <info>  [1692907418.9415] manager: (eth0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/13)
Aug 24 16:03:38 luis-7400 mtp-probe: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2"
Aug 24 16:03:38 luis-7400 mtp-probe: bus: 1, device: 14 was not an MTP device
Aug 24 16:03:38 luis-7400 systemd-udevd[61260]: Using default interface naming scheme 'v249'.
Aug 24 16:03:39 luis-7400 kernel: [19852.454043] ipheth 1-2:4.2 enx020000000000: renamed from eth0
Aug 24 16:03:39 luis-7400 NetworkManager[642]: <info>  [1692907419.0280] device (eth0): interface index 12 renamed iface from 'eth0' to 'enx020000000000'
Aug 24 16:03:39 luis-7400 NetworkManager[642]: <info>  [1692907419.0483] device (enx020000000000): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Aug 24 16:03:39 luis-7400 NetworkManager[642]: <info>  [1692907419.0566] settings: (enx020000000000): created default wired connection 'Conexión cableada 1'
Aug 24 16:03:39 luis-7400 usbmuxd[15422]: [16:03:39.070][1] preflight_worker_handle_device_add: The stored pair record for device 49ab28b8ae516f803c55272ea9338a3660484ada is invalid. Removing.
Aug 24 16:03:39 luis-7400 gnome-shell[2029]: The peer-to-peer connection failed: The name :1.311 was not provided by any .service files. Falling back to the session bus. Your application is probably missing --filesystem=xdg-run/gvfsd privileges.
```

---

