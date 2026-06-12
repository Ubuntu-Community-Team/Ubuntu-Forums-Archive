---
title: "Trackpad and keyboard freezes randomly on MacBook5,1 after system update to 16.10"
date: 2016-12-02
forum: Apple Hardware Users
---

### Post by linus-lin on 2016-12-02
I get random freezes on my laptop's keyboard and trackpad after a system update from 16.04=>16.10. Some times a complete restart is needed after external kb and mouse freeze, other times the keyboard and trackpad function after ~10min. 
I've attempted to reinstall the synaptics driver but this doesn't change the situation.

```

sudo apt install --reinstall xserver-xorg-input-synaptics
```

xinput list:

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; bcm5974                                     id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Apple Computer, Inc. IR Receiver            id=10    [slave  keyboard (3)]
    &#8627; Apple, Inc. Apple Internal Keyboard / Trackpad    id=11    [slave  keyboard (3)]
    &#8627; Built-in iSight                             id=13    [slave  keyboard (3)]
```

/var/logs/kern.log :

```

Dec  2 22:59:03 SilverPear kernel: [25601.572025] ohci-pci 0000:00:04.0: frame counter not updating; disabled
Dec  2 22:59:03 SilverPear kernel: [25601.572032] ohci-pci 0000:00:04.0: HC died; cleaning up
Dec  2 22:59:03 SilverPear kernel: [25601.572075] usb 3-5: USB disconnect, device number 2
Dec  2 22:59:03 SilverPear kernel: [25601.608424] usb 3-6: USB disconnect, device number 3
Dec  2 22:59:03 SilverPear kernel: [25601.684196] bcm5974 3-6:1.2: could not read from device
Dec  2 22:59:48 SilverPear kernel: [25646.344149] usb 2-2: new high-speed USB device number 5 using ehci-pci
Dec  2 22:59:48 SilverPear kernel: [25646.501144] usb 2-2: New USB device found, idVendor=05ac, idProduct=1006
Dec  2 22:59:48 SilverPear kernel: [25646.501148] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec  2 22:59:48 SilverPear kernel: [25646.501151] usb 2-2: Product: Keyboard Hub
Dec  2 22:59:48 SilverPear kernel: [25646.501153] usb 2-2: Manufacturer: Apple, Inc.
Dec  2 22:59:48 SilverPear kernel: [25646.501155] usb 2-2: SerialNumber: 000000000000
Dec  2 22:59:48 SilverPear kernel: [25646.501577] hub 2-2:1.0: USB hub found
Dec  2 22:59:48 SilverPear kernel: [25646.501633] hub 2-2:1.0: 3 ports detected
Dec  2 22:59:49 SilverPear kernel: [25646.792086] usb 2-2.2: new low-speed USB device number 6 using ehci-pci
Dec  2 22:59:49 SilverPear kernel: [25646.906900] usb 2-2.2: New USB device found, idVendor=05ac, idProduct=0221
Dec  2 22:59:49 SilverPear kernel: [25646.906904] usb 2-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec  2 22:59:49 SilverPear kernel: [25646.906907] usb 2-2.2: Product: Apple Keyboard
Dec  2 22:59:49 SilverPear kernel: [25646.906909] usb 2-2.2: Manufacturer: Apple, Inc
Dec  2 22:59:49 SilverPear kernel: [25646.911856] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:06.1/usb2/2-2/2-2.2/2-2.2:1.0/0003:05AC:0221.0008/input/input15
Dec  2 22:59:49 SilverPear kernel: [25646.968780] apple 0003:05AC:0221.0008: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:06.1-2.2/input0
Dec  2 22:59:49 SilverPear kernel: [25646.971828] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:06.1/usb2/2-2/2-2.2/2-2.2:1.1/0003:05AC:0221.0009/input/input16
Dec  2 22:59:49 SilverPear kernel: [25647.028331] apple 0003:05AC:0221.0009: input,hidraw1: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:06.1-2.2/input1
Dec  2 23:00:16 SilverPear gnome-terminal-[27315]: Allocating size to GtkBox 0x5632940ef7b0 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
Dec  2 23:00:22 SilverPear gnome-terminal-[27315]: Allocating size to GtkBox 0x5632940ef7b0 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
Dec  2 23:05:03 SilverPear [2805]: zeitgeist-fts.vala:252: The connection is closed
```

Macbook 5,1 2008 
GeForce 9400M/integrated/SSE2
NVIDIA driver 340.98
UbuntuGnome 16.10

---

### Post by linus-lin on 2016-12-05
Continuing this topic [over here]("http://askubuntu.com/a/847228/328311").

---

