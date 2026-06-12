---
title: "USB devices don't work, how can I enable?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by monocongo on 2007-02-14
I have an external USB drive (Seagate 320GB, SATA in a USB enclosure) which doesn't get recognized when I attach it and turn it on.  The same thing happens when I plug in a USB flash drive (little key chain type).  Is it possible that I need to download a driver for my USB controller, since it seems that no USB devices are working?  

I have a dual boot installation (Windows XP & Ubuntu 6.10).  

Google hasn't helped me find an answer.  If anyone can give me simple instructions on how to go about solving this I'd really appreciate it.  Thanks in advance for any assistance!

--James

---

### Post by mssever on 2007-02-14
Normally, USB works out of the box. The driver is included with Ubuntu.

Please post the stuff relevant to USB from the following command (plug in a USB device or two before issuing the command):
```
lshw | less
```

---

### Post by monocongo on 2007-02-14
From what I can tell my USB controllers are all present and accounted for:

$ sudo lshw -short | grep -i usb
/0/100/13                     bus            IXP SB400 USB Host Controller
/0/100/13/1        usb1       bus            OHCI Host Controller
/0/100/13.1                   bus            IXP SB400 USB Host Controller
/0/100/13.1/1      usb2       bus            OHCI Host Controller
/0/100/13.2                   bus            IXP SB400 USB2 Host Controller
/0/100/13.2/1      usb3       bus            EHCI Host Controller


I have attached two external drives and a flash memory drive through my USB ports, and none of these devices show up in the File Browser window.  In the "Removable Drives and Media Preferences" I have checked the options for mounting removable drives when hot-plugged and for mounting and browsing removable media when inserted.

Any other ideas as to where I can look to find what is amiss?


--James

---

### Post by monocongo on 2007-02-14
Here's the more detailed lshw output relevant to USB:

  *-usb:0
       description: USB Controller
       product: IXP SB400 USB Host Controller
       vendor: ATI Technologies Inc
       physical id: 13
       bus info: pci@00:13.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master cap_list
       configuration: driver=ohci_hcd
       resources: iomemory:fe02d000-fe02dfff irq:201
     *-usbhost
          product: OHCI Host Controller
          vendor: Linux 2.6.17-11-generic ohci_hcd
          physical id: 1
          bus info: usb@1
          logical name: usb1
          version: 2.06
          capabilities: usb-1.10
          configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
  *-usb:1
       description: USB Controller
       product: IXP SB400 USB Host Controller
       vendor: ATI Technologies Inc
       physical id: 13.1
       bus info: pci@00:13.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master cap_list
       configuration: driver=ohci_hcd
       resources: iomemory:fe02c000-fe02cfff irq:201
     *-usbhost
          product: OHCI Host Controller
          vendor: Linux 2.6.17-11-generic ohci_hcd
          physical id: 1
          bus info: usb@2
          logical name: usb2
          version: 2.06
          capabilities: usb-1.10
          configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
  *-usb:2
       description: USB Controller
       product: IXP SB400 USB2 Host Controller
       vendor: ATI Technologies Inc
       physical id: 13.2
       bus info: pci@00:13.2
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ehci bus_master cap_list
       configuration: driver=ehci_hcd
       resources: iomemory:fe02b000-fe02bfff irq:201
     *-usbhost
          product: EHCI Host Controller
          vendor: Linux 2.6.17-11-generic ehci_hcd
          physical id: 1
          bus info: usb@3
          logical name: usb3
          version: 2.06
          capabilities: usb-2.00
          configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s

---

### Post by mssever on 2007-02-14
> **monocongo said:**
> Here's the more detailed lshw output relevant to USB:

  *-usb:0
       description: USB Controller
       product: IXP SB400 USB Host Controller
       vendor: ATI Technologies Inc
       physical id: 13
       bus info: pci@00:13.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master cap_list
       configuration: driver=ohci_hcd
       resources: iomemory:fe02d000-fe02dfff irq:201
     *-usbhost
          product: OHCI Host Controller
          vendor: Linux 2.6.17-11-generic ohci_hcd
          physical id: 1
          bus info: usb@1
          logical name: usb1
          version: 2.06
          capabilities: usb-1.10
          configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
  *-usb:1
       description: USB Controller
       product: IXP SB400 USB Host Controller
       vendor: ATI Technologies Inc
       physical id: 13.1
       bus info: pci@00:13.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master cap_list
       configuration: driver=ohci_hcd
       resources: iomemory:fe02c000-fe02cfff irq:201
     *-usbhost
          product: OHCI Host Controller
          vendor: Linux 2.6.17-11-generic ohci_hcd
          physical id: 1
          bus info: usb@2
          logical name: usb2
          version: 2.06
          capabilities: usb-1.10
          configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
  *-usb:2
       description: USB Controller
       product: IXP SB400 USB2 Host Controller
       vendor: ATI Technologies Inc
       physical id: 13.2
       bus info: pci@00:13.2
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ehci bus_master cap_list
       configuration: driver=ehci_hcd
       resources: iomemory:fe02b000-fe02bfff irq:201
     *-usbhost
          product: EHCI Host Controller
          vendor: Linux 2.6.17-11-generic ehci_hcd
          physical id: 1
          bus info: usb@3
          logical name: usb3
          version: 2.06
          capabilities: usb-2.00
          configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
This is the output with USB device(s) plugged in?

Try this: type ```
less /var/log/messages
``` and hit <shift>F. Then plug and unplug USB devices. Post any output you see.

By the way, it's a lot easier to read posted output if you use the code button before pasting because that preserves formatting.

---

### Post by monocongo on 2007-02-14
Thanks for your help.  I didn't know that there was a code formatting button available for this forum's editor, sorry about that and thanks for pointing it out to me.

Below is the lshw output again, this time formatted, and following that is the output of "tail -f /var/log/messages" after plugging in a few of my USB external drives.

```
$ sudo lshw -C bus
  *-usb:0
       description: USB Controller
       product: IXP SB400 USB Host Controller
       vendor: ATI Technologies Inc
       physical id: 13
       bus info: pci@00:13.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master cap_list
       configuration: driver=ohci_hcd
       resources: iomemory:fe02d000-fe02dfff irq:201
     *-usbhost
          product: OHCI Host Controller
          vendor: Linux 2.6.17-11-generic ohci_hcd
          physical id: 1
          bus info: usb@1
          logical name: usb1
          version: 2.06
          capabilities: usb-1.10
          configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
  *-usb:1
       description: USB Controller
       product: IXP SB400 USB Host Controller
       vendor: ATI Technologies Inc
       physical id: 13.1
       bus info: pci@00:13.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master cap_list
       configuration: driver=ohci_hcd
       resources: iomemory:fe02c000-fe02cfff irq:201
     *-usbhost
          product: OHCI Host Controller
          vendor: Linux 2.6.17-11-generic ohci_hcd
          physical id: 1
          bus info: usb@2
          logical name: usb2
          version: 2.06
          capabilities: usb-1.10
          configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
  *-usb:2
       description: USB Controller
       product: IXP SB400 USB2 Host Controller
       vendor: ATI Technologies Inc
       physical id: 13.2
       bus info: pci@00:13.2
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ehci bus_master cap_list
       configuration: driver=ehci_hcd
       resources: iomemory:fe02b000-fe02bfff irq:201
     *-usbhost
          product: EHCI Host Controller
          vendor: Linux 2.6.17-11-generic ehci_hcd
          physical id: 1
          bus info: usb@3
          logical name: usb3
          version: 2.06
          capabilities: usb-2.00
          configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s

```

```
$ tail -f /var/log/messages
Feb 14 17:39:33 monocongo kernel: [17179794.496000] usb 3-5: new high speed USB device using ehci_hcd and address 13
Feb 14 17:39:44 monocongo kernel: [17179806.152000] usb 3-5: new high speed USB device using ehci_hcd and address 14
Feb 14 17:39:56 monocongo kernel: [17179817.808000] usb 3-5: new high speed USB device using ehci_hcd and address 15
Feb 14 17:40:06 monocongo kernel: [17179828.344000] usb 3-5: new high speed USB device using ehci_hcd and address 16
Feb 14 17:41:47 monocongo kernel: [17179929.324000] usb 3-3: new high speed USB device using ehci_hcd and address 17
Feb 14 17:41:59 monocongo kernel: [17179940.980000] usb 3-3: new high speed USB device using ehci_hcd and address 18
Feb 14 17:42:11 monocongo kernel: [17179952.636000] usb 3-3: new high speed USB device using ehci_hcd and address 19
Feb 14 17:42:21 monocongo kernel: [17179963.172000] usb 3-3: new high speed USB device using ehci_hcd and address 20
Feb 14 17:55:52 monocongo kernel: [17180773.820000] usb 3-4: new high speed USB device using ehci_hcd and address 21
Feb 14 17:56:04 monocongo kernel: [17180785.476000] usb 3-4: new high speed USB device using ehci_hcd and address 22
Feb 14 17:56:15 monocongo kernel: [17180797.132000] usb 3-4: new high speed USB device using ehci_hcd and address 23
Feb 14 17:56:26 monocongo kernel: [17180807.668000] usb 3-4: new high speed USB device using ehci_hcd and address 24

```

Am I mistaken in my assumption that these devices should just show up in the File Browser, automatically mounted, etc.?  If not then maybe these devices are present and I just need to mount them or otherwise make them visible somehow?


--James

---

### Post by mssever on 2007-02-14
You're correct that they should automatically appear when they're plugged in. Mine do.

What's confusing me, though, is that although /var/log/messages shows that the system is seeing the devices, they aren't showing up in lshw. They should be there.

Here are a couple of other things to try.

With the drives plugged in, type ```
mount
``` and see if by any chance they're showing up.

If not, plug in a drive and go to /dev/disk/by-id and see if there's a symlink to the device in that directory. If so, you could set up an fstab entry for each device (see [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")). Of course, if you do this, you lose the automount features--so it's a workaround, not a solution.

---

### Post by monocongo on 2007-02-14
No joy after running mount.

I only see the two devices which are already mounted (plus a few which are not mounted -- partitions of the primary drive which are used by Windows, etc.) when I look at the contents of /dev/disk/by-id.  This is true even though I have three external hard drives and a flash drive plugged into my machine's USB ports.

Is there a command which can be run which will create the device files after polling the USB controllers to find out if they have any devices connected to them?

What's interesting to me is that when I plug in a USB device I get four separate messages from /var/log/messages. For example:
```
Feb 14 20:36:54 monocongo kernel: [17190435.292000] usb 3-5: new high speed USB device using ehci_hcd and address 35
Feb 14 20:37:06 monocongo kernel: [17190446.948000] usb 3-5: new high speed USB device using ehci_hcd and address 36
Feb 14 20:37:17 monocongo kernel: [17190458.604000] usb 3-5: new high speed USB device using ehci_hcd and address 37
Feb 14 20:37:28 monocongo kernel: [17190469.140000] usb 3-5: new high speed USB device using ehci_hcd and address 38

```
Does this indicate a problem, or is this to be expected?

--James

---

### Post by mssever on 2007-02-15
Something certainly is weird. For reference, here's what I get in /var/log/messages when I plug in a USB flash drive: ```
[FONT=Courier New]Feb 15 15:05:27 scott-laptop kernel: [17268996.564000] usb 1-4: new high speed USB device using ehci_hcd and address 45
Feb 15 15:05:27 scott-laptop kernel: [17268996.696000] usb 1-4: configuration #1 chosen from 1 choice
Feb 15 15:05:29 scott-laptop kernel: [17268997.792000] usbcore: registered new driver libusual
Feb 15 15:05:29 scott-laptop kernel: [17268997.864000] Initializing USB Mass Storage driver...
Feb 15 15:05:29 scott-laptop kernel: [17268997.864000] scsi0 : SCSI emulation for USB Mass Storage devices
Feb 15 15:05:29 scott-laptop kernel: [17268997.864000] usbcore: registered new driver usb-storage
Feb 15 15:05:29 scott-laptop kernel: [17268997.864000] USB Mass Storage support registered.
Feb 15 15:05:34 scott-laptop kernel: [17269002.864000]   Vendor: LEXAR     Model: JUMPDRIVE SPORT   Rev: 2000
Feb 15 15:05:34 scott-laptop kernel: [17269002.864000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Feb 15 15:05:34 scott-laptop kernel: [17269002.932000] SCSI device sda: 248928 512-byte hdwr sectors (127 MB)
Feb 15 15:05:34 scott-laptop kernel: [17269002.932000] sda: Write Protect is off
Feb 15 15:05:34 scott-laptop kernel: [17269002.936000] SCSI device sda: 248928 512-byte hdwr sectors (127 MB)
Feb 15 15:05:34 scott-laptop kernel: [17269002.936000] sda: Write Protect is off
Feb 15 15:05:34 scott-laptop kernel: [17269002.936000]  sda: sda1
Feb 15 15:05:34 scott-laptop kernel: [17269002.976000] sd 0:0:0:0: Attached scsi removable disk sda
Feb 15 15:05:34 scott-laptop kernel: [17269002.988000] sd 0:0:0:0: Attached scsi generic sg0 type 0[/FONT]
```As far as setting those symlinks up goes, they're created by udev, I believe. But it appears that your problem is occurring earlier, since it isn't getting a device name, as far as I can tell. You might try iterating through /dev/sda, /dev/sdb, etc and see if you can mount manually.

Really, this is an area that I don't know a whole lot about. My USB devices have always been recognized.

---

### Post by easy_target on 2007-02-17
Try this:

```
sudo modprobe -r ehci_hcd
```

and try plugging your device again.

It worked for me and it seems to be a bug with ehci_hcd module.

I am currently on the process of blacklisting it but  I dont know if it&#347; going to affect other usb devices.

---

### Post by monocongo on 2007-02-18
I have made my way around these USB problems by using the kernel option 'irqpoll' at boot time.  I have no idea as to what this option does, but it has fixed me right up and now my system is running like a champ with Ubuntu.  Goodbye Microsoft.  Further details are **[here]("http://www.ubuntuforums.org/showthread.php?t=81153").**

--James

---

### Post by jimrothstein on 2007-02-23
I am having usb problems very simlar to monocongo (no mouse, no flash drives), but irqpoll isn't fixing them.

My problems began when I upgraded to 2.6.15-28-386, running on Acer Aspire 5102 (AMD Turion).
Booting with prior kernel doesn't fix.

Do I have hardware problem?

Here's less /var/log/messages  as I remove and insert a usb memory stick: **(booting with irqpoll)**

```
Feb 24 10:26:00 localhost kernel: [17180386.848000] usb 3-7: new high speed USB device using ehci_hcd and address 6
Feb 24 10:27:15 localhost kernel: [17180461.692000] usb 3-1: new high speed USB device using ehci_hcd and address 10
```
  

```
sudo lshw -short | grep -i usb
/0/100/13                     bus         IXP SB400 USB Host Controller
/0/100/13/1        usb1       bus         OHCI Host Controller
/0/100/13.1                   bus         IXP SB400 USB Host Controller
/0/100/13.1/1      usb2       bus         OHCI Host Controller
/0/100/13.2                   bus         IXP SB400 USB2 Host Controller
/0/100/13.2/1      usb3       bus         EHCI Host Controller

```

Appreciate any thoughts.

Thanks.

---

### Post by frozenjim on 2008-01-09
```
modprobe -r ehci_hcd
``` 
This has always worked for me when I need to attach my external USB drive.

Everything else works great - including USB thumb drives.  It's only the external HDD enclosure that requires this little "kick" to get it running.  Usually, I don't even have to reconnect the drive; just type in the command and "bingo" the drive shows up.

Can anyone tell me WHY this is the case?  This little fix has been around since before GUTSY.  I sure don't like the feel of it when I'm bragging up my Linux box.

---

