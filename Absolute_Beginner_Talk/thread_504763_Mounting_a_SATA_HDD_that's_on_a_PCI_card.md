---
title: "Mounting a SATA HDD that's on a PCI card"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by theonlyalterego on 2007-07-19
I have an older PC with 4 IDE HDDs mounted. I have added a PCI SATA card to try and mount a newer SATA drive. Ubuntu can see the SATA card, but I'm not sure how to mount the drive.

Any help would be appreciated, I couldn't find much after searching the forums =/ If more info is required just let me know what you need.

```

~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0d.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0d.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0d.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:0f.0 Mass storage controller: Promise Technology, Inc. PDC20518/PDC40518 (SATAII 150 TX4) (rev 02)
00:10.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```

---

### Post by Rocket2DMn on 2007-07-19
What happens when you run
```
sudo fdisk -l
```
Should it be terribly different from running hard drives through USB?

---

### Post by reckless2k2 on 2007-07-19
if the pci card is working, you should see it already. have you check storage media? or device manager?

---

### Post by theonlyalterego on 2007-07-19
It lists only the HDDs that are currently mounted...

hda - contain my ubuntu install
hdb - contains storage only (no OS's installed here)

the last two I'm planning on wiping clean, they're old HDDs containing elderly windows installs.

```

ego@ub-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1190     9558643+  83  Linux
/dev/hda2            1191        1244      433755    5  Extended
/dev/hda5            1191        1244      433723+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161   42  SFS

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdd: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        3649    29310561    7  HPFS/NTFS

```

---

### Post by Rocket2DMn on 2007-07-19
Does the harddrive need to have specific jumper settings?

---

### Post by theonlyalterego on 2007-07-19
You mean like a specific master/slave setting? I believe it's currently set as a slave drive. 

I'm at work SSH-Tunneled+VNC into the machine, so I can't check it specifically. But it was previously set as a 'storage' disk on my old windows box, so it shouldn't be set as the master.

Here's a screenshot of the device manager, looks to me like it's finding the SATA PCI card but not the SATA HDD...

[IMG]http://img329.imageshack.us/img329/5885/satage5.png[/IMG]

---

### Post by Rocket2DMn on 2007-07-19
When you get a chance to get your hands on the drive, you should try setting the jumpers to Cable Select or Master if that doesn't work.  These jumpers relate to the hardware configuration in the tower, not the software use of the drive.

---

### Post by theonlyalterego on 2007-07-19
Turns out the power cable was loose >.< *sigh* nothing like an easy fix. thanks for all the help though :)


For the record I'm amazed how easy that was... once everything was plugged in properly =)

---

