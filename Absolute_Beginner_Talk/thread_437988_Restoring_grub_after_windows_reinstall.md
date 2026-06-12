---
title: "Restoring grub after windows reinstall"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Crushyerbones on 2007-05-09
I know I shouldn't have done this but Windows XP had a catastrophic trojan attack which left nothing to be salvaged, leaving my only hope to be a complete reformat of the HDD I had it installed in.

Here's my problem... I had Ubuntu 7.04 installed on my primary slave and XP on my Primary Master. It's now exactly the same as it was before, only windows overrode the grub bootloader.

Grub is still on my Ubuntu partition, I just have the windows loader instead, all I need is the "link" which makes the grub bootloader show up instead.

I have tryed the supergrub disk (maybe I got the name wrong :confused: ). And for some reason it doesn't seem to do anything... I just get a gbd (again, maybe I got the name wrong) succsesfull message and I get tossed into the restore grub menu. I have managed to make the old grub load tough, and even boot Linux through it, but only by using the CD.

Any help would be appreciated since it's about the 12th time I've reinstalled Ubuntu and this time I finally got everything working as I'd like... :( I just don't feel like going through all the trouble to get mouse buttons, web cams, wacoms and other stuff working again...

---

### Post by mejy on 2007-05-09
Booting onto the Ubuntu live cd and typing 'sudo grub-install /dev/[sda/sdb etc]' should do the trick.

---

### Post by Kobalt on 2007-05-09
How to recover Grub after a Windows install : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by Crushyerbones on 2007-05-09
> **Kobalt said:**
> How to recover Grub after a Windows install : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

Maybe I'm just unlucky but that was the first thing I tried and BIOS got stuck on an endless loop of "Loading Grub stage 2" messages. (They filled the whole screen and kept going)

> Booting onto the Ubuntu live cd and typing 'sudo grub-install /dev/[sda/sdb etc]' should do the trick.

Does that mean if I'm booting from my sda drive I should type 'sudo grub-install /dev/[sda]' ? Or do I remove the brackets?

Well, off I go to try it, wish me luck

---

### Post by Kobalt on 2007-05-09
That would be without the brackets.

---

### Post by Crushyerbones on 2007-05-09
I'm now on a 7.04 final Live CD and after executing 

```
sudo grub-install /dev/hdc1
```

I get this

```
Could not find device for /boot: Not found or not a block device.

```

I've tried different alternatives for hdc1, including other partitions and removing the 1. The result is always the same.


If I sudo fdisk-l I get this

```
Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4660    37431418+  83  Linux
/dev/hdd2            4661        4865     1646662+   5  Extended
/dev/hdd5            4661        4865     1646631   82  Linux swap / Solaris

```

Edit: Just thought I'd mention I want the bootlader installed on hdc1 if possible

---

### Post by u04f061 on 2007-05-09
boot live
first of all check where your linux is installed by typing

sudo fdisk -l

from here see the linux partitions.
if you have only one linux partition , then sure it is where your linux is installed.
let it is /dev/hda2.
then  type 
> sudo -i 
it will give you a complete root access.
then 
> 1-mkdir /mnt/root
2-mount -t ext3 /dev/hda2  /mnt/root
3-grub-install --root-directory=/mnt/root  /dev/hda  -recheck

if you get some error in command 3 then remove -recheck option
if you donot get success in following these steps , plz respond quickly i would try to troubleshoot

---

### Post by Crushyerbones on 2007-05-09
Thank you for your answer :) I'm just about to try the method on the 5th post here:
[http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub)

Everything seemed ok so far, If it doesn't work I'll try it your way... Be right back...

---

### Post by Crushyerbones on 2007-05-09
There, it's fixed :) Thanks for all the help, method on that other thread worked flawlessly

---

### Post by elladan99 on 2008-01-25
i'm into panic mode now til i came across this thread. i'm in the same situation so gonna try the solution posted  and update you guys. wish me luck.

---

### Post by jukingeo on 2008-07-23
Hello all, 

I accidentally deleted Windows through a partitioning mistake.  However, I managed to get it back up and running.  Now the new problem is that Windows "Replaced" Grub with it's own boot loader in exactly the same fashion that Crushyerbones had as I quoted below.

So my current problem is the exact same circumstance and I would like to get Grub back.


> **Crushyerbones said:**
> 

Here's my problem... I had Ubuntu 7.04 installed on my primary slave and XP on my Primary Master. It's now exactly the same as it was before, only windows overrode the grub bootloader.

Grub is still on my Ubuntu partition, I just have the windows loader instead, all I need is the "link" which makes the grub bootloader show up instead.




This is my current drive set up:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32c632c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7333    58902291    7  HPFS/NTFS
/dev/sda2            7334        9726    19221772+   b  W95 FAT32
omitting empty partition (5)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf364

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1837    14755671   83  Linux
/dev/sdb2            1838       13995    97659135   83  Linux
/dev/sdb3           13996       60800   375961162+   5  Extended
/dev/sdb4   *       54722       60800    48829567+   b  W95 FAT32
/dev/sdb5           13996       32231   146480607   83  Linux
/dev/sdb6           32232       54465   178594573+  83  Linux
/dev/sdb7           54466       54721     2056288+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

I have seen this guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

I have tried to follow it, but being only a month or so on Ubuntu, I am not making sense of it and need assistance.

So it goes without saying that I would like to fix Grub the EASIEST way possible.

Thank You,

Geo

---

