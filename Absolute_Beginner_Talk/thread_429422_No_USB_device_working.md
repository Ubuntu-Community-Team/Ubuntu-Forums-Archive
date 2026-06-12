---
title: "No USB device working"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by yuehan on 2007-05-01
Hi, 
I just installed 7.04, everything works (wifi, CD drive, correct resolution) except USB devices - I tried two flash disks, card reader and camera and nothing happens, they don't get automounted and don't show up as sda, even their LEDs won't light up (on one memory stick it will). USB mouse lights up and after a minute or so even moves the cursor but so erraticaly that it's unusable. 

Mine is a dual boot system (Fujitsu-Siemens Amilo L7310GW) and under WinXP everything was OK. I already tried booting with the devices connected but apart from boot taking much longer time nothing changed.

Any help very much appreciated, life without USB is a hard life...

This is when I had card reader, flash disk and mouse connected:
```

yuehan@ubuntu:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
yuehan@ubuntu:~$ sudo lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 15d9:0a33  
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by mikeyphi on 2007-05-01
Try the following:
Under System - Preferences - Removable Drives and Media    make sure boxes are ticked.

If still no action:
Under Places - Computer  (if device shown} right click and select Mount

If still no action:
open a terminal and enter -

sudo mount -t vfat /dev/sdda1 /mnt

(change the 'sda1' to the correct 'sd**')  if you don't know the label use this command to find - 

ls -l /dev/sd*

(that's 2xsmall l not L or 1 !!)

remember to use -

unmount /dev/sda1

before removal

Good luck

---

### Post by yuehan on 2007-05-04
My problem is that USB is not working at all. What finally helped was PCI=NOACPI parameter but then my wifi stopped working, so now I'm left with choice either USB or WiFi. Hmm...

---

### Post by imon9 on 2007-05-04
hi, 

just trying to help u here... maybe you can try a recompiled kernel without the experimental USB-suspend feature...

you can get the .deb easy installer at the following thread.... no worries to instlal it, U can always uninstall if it doesnt helps

here is the link:
[http://ubuntuforums.org/showthread.php?t=432130](http://ubuntuforums.org/showthread.php?t=432130)

---

### Post by airbornespent on 2007-05-04
Try putting in USB devices after a full restart. There is a problem right now where USB does not work at all after suspending and resuming on alot of laptops.

---

### Post by yuehan on 2007-05-05
Hey guys, thanks for trying to help me, unfortunately none of the solutions worked. 
So now I have two entries in Grub, one for Ubuntu with USB and one for Ubuntu with WiFi, not very comfortable but I can live with it. When I boot with the pci=noacpi parameter, all USB devices work but WiFi adaptor isn't found. Here's some listings which I don't really expect anybody to study, but maybe someone had similar problems - I can't be the only one running Ubuntu on FS Amilo, can I?

iwconfig
```

lo        no wireless extensions.
eth0      no wireless extensions.
wifi0     no wireless extensions.

```

and following section (which is here when I boot without the pci=noacpi parameter) is missing
```
ath0      IEEE 802.11g  ESSID:"eircom1750 0614"  Nickname:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0F:CC:3E:8E:40   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=27/94  Signal level=-66 dBm  Noise level=-93 dBm
          Rx invalid nwid:9263  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and dmesg says
```

[   21.688000] ath_hal: module license 'Proprietary' taints kernel.
[   21.688000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   22.724000] wlan: 0.8.4.2 (0.9.3)

[   23.056000] ath_pci: 0.9.4.5 (0.9.3)
[   23.056000] PCI: Enabling device 0000:00:06.0 (0000 -> 0002)
[   23.056000] PCI: No IRQ known for interrupt pin A of device 0000:00:06.0. Please try using pci=biosirq.
[   23.056000] IRQ handler type mismatch for IRQ 0

[   23.056000] current handler: timer
[   23.056000]  [<c01540fe>] setup_irq+0x12e/0x1e0
[   23.056000]  [<dcb39520>] ath_intr+0x0/0xc20 [ath_pci]
[   23.056000]  [<c0154253>] request_irq+0xa3/0xc0
[   23.056000]  [<dcb3bf8d>] ath_pci_probe+0x1ad/0x3b0 [ath_pci]
[   23.056000]  [<c01b8ede>] sysfs_create_link+0x6e/0x160
[   23.056000]  [<dcb3bde0>] ath_pci_probe+0x0/0x3b0 [ath_pci]
[   23.056000]  [<c01fba76>] pci_device_probe+0x56/0x80
[   23.056000]  [<c0257a66>] really_probe+0x66/0x190
[   23.056000]  [<c0257bd9>] driver_probe_device+0x49/0xc0
[   23.056000]  [<c0257dae>] __driver_attach+0x9e/0xa0
[   23.056000]  [<c0256f3b>] bus_for_each_dev+0x3b/0x60
[   23.056000]  [<c0257904>] driver_attach+0x24/0x30
[   23.056000]  [<c0257d10>] __driver_attach+0x0/0xa0
[   23.056000]  [<c02572cb>] bus_add_driver+0x7b/0x1a0
[   23.056000]  [<c01fbc44>] __pci_register_driver+0x74/0xc0
[   23.056000]  [<dc853030>] init_ath_pci+0x30/0x54 [ath_pci]
[   23.056000]  [<c014421d>] sys_init_module+0x15d/0x1ba0
[   23.056000]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[   23.056000]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[   23.056000]  [<c02e0033>] xfrm_state_find+0x4e3/0x570
[   23.056000]  =======================
[   23.056000] wifi%d: request_irq failed

```

---

