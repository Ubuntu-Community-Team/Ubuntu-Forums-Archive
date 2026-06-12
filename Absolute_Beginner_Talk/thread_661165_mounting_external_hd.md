---
title: "mounting external hd"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by JoeyHustle on 2008-01-07
ok, i have browsed these forums for the answer but havent really found it so heres my question. i bought a 300gb hd but its not usb ita esata where i had to install a card into my comp for it to connect to. so my question is the easiest way to mount it. also its a one touch so am i going to have to unmount it and remount it as i turn it on and off. thanks.

---

### Post by tech9 on 2008-01-07
> **JoeyHustle said:**
> ok, i have browsed these forums for the answer but havent really found it so heres my question. i bought a 300gb hd but its not usb ita esata where i had to install a card into my comp for it to connect to. so my question is the easiest way to mount it. also its a one touch so am i going to have to unmount it and remount it as i turn it on and off. thanks.

try this...

plug in your portable device

open terminal and type
```
fdisk -l
```
find out the what the partition is labeled as, example: /dev/sda3

to mount it
```
sudo mount /dev/"partition"
```to unmount it
```
sudo umount /dev/"partition"
```

---

### Post by JoeyHustle on 2008-01-07
hey thanks, there are three diff listings how do i know which one it is. there is a IDE disk, SCSI disk, and a PS/2 ESDI disk. thanks.

---

### Post by JoeyHustle on 2008-01-09
hey guys im kinda confused,...
 sudo mount /dev/sda5
mount: mount point none does not exist

doesnt make sense but if someone could help me out that would be cool. thanks

---

### Post by tech9 on 2008-01-09
> **JoeyHustle said:**
> hey guys im kinda confused,...
 sudo mount /dev/sda5
mount: mount point none does not exist

doesnt make sense but if someone could help me out that would be cool. thanks


can you post your output of 

```
fdisk -l
```

---

### Post by JoeyHustle on 2008-01-09
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

i hope thats what you need. by the way the hd worked fine in windows. thanks again.

---

### Post by geirha on 2008-01-09
That there looks like the hd you've installed ubuntu on. Could you post the entire output of ```
sudo fdisk -l
``` I think the external hd is one of the other two

Have you partitioned and formatted it yet?

---

### Post by JoeyHustle on 2008-01-09
no i havent done anything to the external yet. 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

the one ubuntu is on is an internal 40 gig. the hard drive im trying to mount is a 300gb seagate esata external. thanks.

---

### Post by geirha on 2008-01-10
If that's the entire output of "sudo fdisk -l", then either your machine, or ubuntu is unable to detect your SATA-card or your external harddrive. First off, what's the output of this command? It should show your sata card. ```
lspci
```

---

### Post by tech9 on 2008-01-10
> **geirha said:**
> If that's the entire output of "sudo fdisk -l", then either your machine, or ubuntu is unable to detect your SATA-card or your external harddrive. First off, what's the output of this command? It should show your sata card. ```
lspci
```

sorry, I have been out for a while,

I agree...

post your output of 
```
lspci
```If your SATA device is not showing then thats the problem... another good test is run the fdisk -l when your drive is connected and then unconnected. See if one of your partitions drop off.

---

### Post by JoeyHustle on 2008-01-10
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:07.0 Mass storage controller: Promise Technology, Inc. PDC40775 (SATA 300 TX2plus) (rev 02)
02:08.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

the hd im trying to mount is the mass storage controller.

---

### Post by buccaneere on 2008-01-10
> **JoeyHustle said:**
> ok, i have browsed these forums for the answer but havent really found it so heres my question. i bought a 300gb hd but its not usb ita esata where i **had to install a card** into my comp for it to connect to. so my question is the easiest way to mount it. also its a one touch so am i going to have to unmount it and remount it as i turn it on and off. thanks.

You're talkin' about an IDE controller card??? Never mind - They beat me to the punch - lspci...

Places/Computer (from top panel) ... You sure the volume isn't showin' up there? If it is, see if you can right click, and get the mount option...

---

### Post by JoeyHustle on 2008-01-10
yeah no, its not showing up there.

---

### Post by buccaneere on 2008-01-10
post return for :
[HTML]sudo gedit  /etc/mtab[/HTML]

---

### Post by JoeyHustle on 2008-01-10
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

---

### Post by buccaneere on 2008-01-10
> **JoeyHustle said:**
> /dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

Your controller card should be showing up here as

/dev/sdb1 <mount point> <file type> <mount permissions> <dump> <fsck>

Enter:
[HTML]sudo mount /dev/sdb1[/HTML]

I'm guessin' sd**b**1, since your local drive appears to be sda1...

---

### Post by buccaneere on 2008-01-10
Is there anything on this disk? Has it been formatted in Windows? Or with any file system format?

If not, it will need to be formatted...

---

### Post by JoeyHustle on 2008-01-11
there is stuff on it from windows but i dont need the stuff. i went into gparted and it couldnt find the drive so i cant format it.

---

### Post by auzzie on 2008-01-11
Im using a one touch too, it comes up as sdb1 but i have no problem, i can just "almost" use it as plug and play, just after a while i have to force a mount using the following command. 
```

sudo mount -t ntfs-3g /dev/sdb1 /media/WinStorage -o force

```

Where WinStorage is the external HDD and it was partitioned with a ntfs partition.
I hope this helps

---

### Post by buccaneere on 2008-01-11
> **JoeyHustle said:**
> there is stuff on it from windows but i dont need the stuff. i went into gparted and it couldnt find the drive so i cant format it.

That means it has ntfs file system type/formatting on it.

If you're sure nothing is on it that you need to keep, you can then format it ext2/ext3.

[HTML]sudo mkfs /dev/sdb1[/HTML]

---

