---
title: "Some Help with my Bootloader"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Fenopy on 2007-12-11
Alright, to start, I have the following Operating Systems Installed:
Windows XP - hda1
Windows Vista - hda2
Fedora 8 - hda5
swap - hda6
Ubuntu 7.10 - hda7

Windows XP - hdb1 - (This is an old installation, I will eventually get rid of this... but not for now)
NTFS Storage Partition - hdb5

Also, I hidden, unknown partition (according to 'Logical Volume Management') under hda3

Right now I have my BootLoader set up as this:
```
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional (Old Installation)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=186a573d-bb0b-4a78-b5bc-f65e3343dcaa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Fedora (2.6.23.1-42.fc8)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.23.1-42.fc8 ro root=LABEL=/ rhgb quiet 
initrd		/boot/initrd-2.6.23.1-42.fc8.img
savedefault
boot
```
**Which boots:**
Windows Vista Loader
Windows Vista Loader
Ubuntu 7.10
Windows Vista Loader
Fedora 8

(Now, the Windows Vista Loader has: Windows Vista & Windows XP (Old Installation) listed)

Ok, so how do i configure the BootLoader so I can boot directly into Windows XP (Both Versions) and into Vista without even seeing the Vista Loader?
Also, I am not able to access my new XP install AT ALL. So there is something wrong with the HDA positions I have it in.

I hope this is easy to understand... Please, ask questions if it isn't! And Thank You So Much for Any Help!!!

---

### Post by p_quarles on 2007-12-11
This looks like more of a Windows issue than a Grub issue, and Windows isn't my area of greatest knowledge, but I'll take a stab at this.

Based on your menu.lst contents, it looks like you are attempting to use the first partition to load both Vista and XP (new). According to the partition sceme you described, Vista should boot from (hd0,1), and XP should boot from (hd0,0). Oddly, though, you're saying that Vista loads okay, but that XP does not. The first thing that comes to mind is that your partitions may be slightly different than you think. Can you verify the partition table by pasting the output of the following?:
```
sudo fdisk -l
```

---

### Post by Fenopy on 2007-12-11
> **p_quarles said:**
> This looks like more of a Windows issue than a Grub issue, and Windows isn't my area of greatest knowledge, but I'll take a stab at this.

Based on your menu.lst contents, it looks like you are attempting to use the first partition to load both Vista and XP (new). According to the partition sceme you described, Vista should boot from (hd0,1), and XP should boot from (hd0,0). Oddly, though, you're saying that Vista loads okay, but that XP does not. The first thing that comes to mind is that your partitions may be slightly different than you think. Can you verify the partition table by pasting the output of the following?:
```
sudo fdisk -l
```

Where do I input that?
I am just starting to learn this stuff, and understand some of it, except for that cmd line stuff that people keep posting...
And once I get off work I will go home and try that then and let you know what comes out of it.

---

### Post by p_quarles on 2007-12-11
You type that in the terminal, which you can open either from the application menu or by pressing alt-F1. fdisk is a program that manages partitions, and the -l option specifies that you want to list the partitions that are available. "sudo" means that you'll be running this command as the root user. You'll be asked for your password before you can do this.

---

### Post by spiderbatdad on 2007-12-11
you would open a terminal from your gnome desktop Applications-->Accessories-->Terminal.
then in the terminal also called CLI (command line interface) you would enter the above command.

---

### Post by Fenopy on 2007-12-11
Well.. It all seems to look the same as I described it...
```

Disk /dev/hda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc86bc86b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         637     5116671    7  HPFS/NTFS
/dev/hda2             638        2932    18432000    7  HPFS/NTFS
/dev/hda3            2932        5238    18522945+   f  W95 Ext'd (LBA)
/dev/hda5            2933        4079     9213277+  83  Linux
/dev/hda6            4080        4144      522081   82  Linux swap / Solaris
/dev/hda7            4145        5238     8787523+  83  Linux

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10321031

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2197    17647371    7  HPFS/NTFS
/dev/hdb2            2198       14945   102398310    f  W95 Ext'd (LBA)
/dev/hdb5            2198       14945   102398278+   7  HPFS/NTFS

```

[[IMG]http://img132.imageshack.us/img132/4567/fdisktq8.th.png[/IMG]](http://img132.imageshack.us/my.php?image=fdisktq8.png)

I still dont know WTF this is: ```
/dev/hda3            2932        5238    18522945+   f  W95 Ext'd (LBA)
```

---

### Post by p_quarles on 2007-12-11
The volume labeled /dev/hda3 is your "extended" partition. You can only have up to 4 primary partitions on a disk drive. To go beyond that, you need to have an extended partition, within which live your "logical" partitions (in this case -- your Fedora, Ubuntu, and Linux Swap partitions).

Okay -- here's what I would try. I think you may be able to fix this by editing the boot file. First, though, back it up:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
Now edit the file:
```
gksudo gedit /boot/grub/menu.lst
```
Once that's loaded, change this entry:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
```
To this:
```
title		Microsoft Windows XP Professional
root		(hd0,1)
```
I'm not absolutely certain that this will work, but this is based on my (semi-)educated guess that dev/hda2 is your XP partition.

The problem I can foresee here, though, is that Vista has its own boot manager, and I'm not exactly sure how that works.

---

### Post by Fenopy on 2007-12-11
```
Error 1: Filename must be either an absolute pathname or blocklist

Press any key to continue...
```



And it goes back to the boot screen...


EDIT:
Ah ha!
I tried chaning things around, changed Chainloader back to +1 (dont know why i changed it)
and i got:

```

Starting up...

BOOTMGR is missing
Press Ctrl+Alt+Del to restart

```

I know that is a Windows Error... I would assume it is up to me to fix that one now... (Boot.ini error I assume)

---

### Post by p_quarles on 2007-12-11
> **Fenopy said:**
> ```
Error 1: Filename must be either an absolute pathname or blocklist

Press any key to continue...
```



And it goes back to the boot screen...
Okay . . . can you provide some more context? When are you seeing this message? After starting the computer? After trying to load XP? Trying to load anything?

---

### Post by Fenopy on 2007-12-11
It happens when I select the Windows XP OS to load

(Please look at my edit in the above post)

---

### Post by p_quarles on 2007-12-11
> **Fenopy said:**
> It happens when I select the Windows XP OS to load

(Please look at my edit in the above post)
Yeah, that makes sense. I noticed that the output of fdisk -l indicated that that drive wasn't bootable, so it's probably just a matter of fixing that. Like I said, I don't know enough about Windows to help you with that. I understand, though, that the [Windows Discussions]("http://ubuntuforums.org/forumdisplay.php?f=170") sub-forum here is actually a pretty good resource.

---

### Post by Fenopy on 2007-12-11
I am fairly proficient in Windows... Which is why this Linux stuff is so very foreign to me... But i like it...

I think I am going to put it on my Xbox as a second OS... lolz

Sadly... I am going to have to redo my entire hard disk.
I made my XP Partition too small...
But the problem was:
XP was taken over by Vista, therefore making it unbootable directly. I needed to go through the boot loader that Vista has.
So i am thinking, that for a solution, I am going to load Vista first (so it thinks it is alone)
Then XP, then Fedora (disabling GRUB), then Ubuntu, letting it handle GRUB and boot loader.

Thank You SOOOOO much for the FAST responses and help!!!

---

### Post by p_quarles on 2007-12-11
Hey, no problem. 

FWIW, it might make sense to look into virtualization, especially if your box has a lot of memory. Not all hardware will work correctly inside a VM environment, but you still have the host OSes for that. It can save a lot of rebooting time.

---

