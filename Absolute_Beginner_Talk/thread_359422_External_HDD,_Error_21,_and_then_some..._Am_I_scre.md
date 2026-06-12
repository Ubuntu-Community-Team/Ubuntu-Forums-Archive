---
title: "External HDD, Error 21, and then some... Am I screwed?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Kougaiji on 2007-02-12
Alright, I'm a new user here, and COMPLETELY new to linux. Today I was compelled to install Ubuntu onto my external USB hard drive. Well... Now when I turn on the computer, it won't boot an OS. I see a grub error message saying "error 21" each time I boot. The only thing that will actually boot is the Live CD, which is what I'm using to post this message.

Alright, here's the situation: I've got 2 internal hard drives (the one with Windows XPsp2 is C:\ with a FAT32 filesystem, and the second is just storage with NTFS) and one external (8 gigabytes, completely unused, that were formatted as ext3 when I installed ubuntu onto it). After the installation, I restarted the computer, and nothing boots. Error 21, and all that junk.


Could anyone please help me? Remember, I am a complete Linux newbie, and I haven't had to mess around with boot settings much in the past, so try not to give me a technical explanation that will go way over my head..?


Thanks in advance..

---

### Post by Terry of Astoria on 2007-02-12
Don't worry. You aren't screwed. You can easily and quickly restore the MBR with a windows boot disc or even Win 98 boot floppy. Please wait for more info from smarter folks than me. I'm sure someone will have more info about whether Ubuntu can run from a USB drive.
  However, here's how to restore the MBR using windows boot CD or floppy. Just boot it up and type ```
fdisk /mbr
``` Do wait for more advice first though.

---

### Post by logos34 on 2007-02-12
Yeah, relax, windows is still there, it's just that even though you installed ubuntu to usb the grub bootloader wants to go on mbr of the internal drive...it just overwrote winxp ntldr...You can easily restore it by booting from the winxp cd, going into the recovery console and doing 'fixmbr' precedure or what the above poster suggested. (In which case you will have to reinstall grub on the usb).

Open a terminal and type this command and post the output:
> sudo fdisk -l

Are you sure your bios supports booting from usb device?

---

### Post by Kougaiji on 2007-02-12
> **logos34 said:**
> Yeah, relax, windows is still there, it's just that even though you installed ubuntu to usb the grub bootloader wants to go on mbr of the internal drive...it just overwrote winxp ntldr...You can easily restore it by booting from the winxp cd, going into the recovery console and doing 'fixmbr' precedure or what the above poster suggested. (In which case you will have to reinstall grub on the usb).

Open a terminal and type this command and post the output:


Are you sure your bios supports booting from usb device?


fdisk results
> Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2491    20008926    c  W95 FAT32 (LBA)

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sda: 8589 MB, 8589934592 bytes
64 heads, 32 sectors/track, 8192 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      912975      995343    84344761   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      830821     1743849   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?           2           2           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4         1409025     1409050       26207+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


I'm sure my BIOS supports booting from USB device.

I think I'm getting close to being able to boot ubuntu, but I need to know something... I'm going to reinstall ubuntu (and with it: grub) onto the usb disk. When installing via the Live CD, I have an option of where to install grub (such as hd0 [default], hd1, etc). If I want to install it on my USB device, what label should I pick? Remember, I have 2 internal hard drives, and according to the installer, the usb drive is labeled as (sdb). What determines the labeling order? Should I choose location (sdb) because that's where the OS is going based on the installer, or should I pick (hd2) because it's a usb device after 2 harddrives, or should I pick (hd**n**) where **n** is the hard drive # based on which of the three drives I give booting priority to?

I know how to change boot priority and most BIOS options, so I know how to set it to boot from USB drive now... however, I think Ubuntu's not booting because grub is not installed on the drive it's being booted from.



**edit**:nevermind, according to fdisk the USB drive is labeled (sda) not (sdb).

*confirmed*: yeah, I'm at step 6 of the installer again and it says (sda) after all. Although I swore it said (sdb) last time around. Anyway, still: what label should I pick for where to install grub?

---

### Post by logos34 on 2007-02-12
pick /dev/sda...it has to go to the usb, it's the only possibility (no other usb or sata)...Grub will probably id it as hd2 (or hd1 considering it's the second bootable disk).

---

### Post by logos34 on 2007-02-12
If you're still having trouble, try the installation again but this time unplug your ide drives.  This way the installer will have no choice but to put grub on the usb drive.  Not a particularly elegant way but it works.  Then all you need to do is add entries for your windows partitions to your fstab file so they automount.

---

### Post by Kougaiji on 2007-02-12
Ok I've set my external to be the second hard drive by booting priority via BIOS (just to be sure that hd1 works). I'm about to try again by selecting the grub location to be (hd1). Selecting the location to be (sda) when installing grub didn't work - figured I would try that until I got a response.

Any other words of advice before/while I install?

---

### Post by logos34 on 2007-02-12
sorry for not getting back sooner...you can try hd1 if you don't want to do what I suggested and disconnect your other drives--that's the surest way...when you mix ide with usb and/or sata grub sometimes will designate drives by boot priority/sequence, other times ide drives first then sata or usb.  However, once you get it properly installed you will probably want to change the usb drive to boot first rather than second, so that when you start up you will boot straight to grub on the usb if it's turned on/connected; of it's not then you will boot from the windows drive.  Unless of course you prefer choosing the external through the bios every time you want to use ubuntu.

---

### Post by Kougaiji on 2007-02-12
> **logos34 said:**
> sorry for not getting back sooner...you can try hd1 if you don't want to do what I suggested and disconnect your other drives--that's the surest way...when you mix ide with usb and/or sata grub sometimes will designate drives by boot priority/sequence, other times ide drives first then sata or usb.  However, once you get it properly installed you will probably want to change the usb drive to boot first rather than second, so that when you start up you will boot straight to grub on the usb if it's turned on/connected; of it's not then you will boot from the windows drive.  Unless of course you prefer choosing the external through the bios every time you want to use ubuntu.

Well designating it by boot sequence didn't work. It installed successfully... but when I try to boot off the USB drive, nothing really happens. I get a flashing "_" cursor that moves down a line once... and things just stay there. I've also made XP bootable again, and I'm back on it right now to write the post. But the fact that MBR works now doesn't seem to have made a difference in starting up Ubuntu.

I had no idea when I was doing this that it was such an obstacle to boot linux off an external drive. 

Well, anyway, here's what I've done now:
I've cleared my 2nd internal hard drive to have a good 51GB of free space.
I'm downloading Fedora Core 6 (just as a second option at the moment).

I'm thinking of giving up on trying to make it work on the USB drive right now, and instead just partitioning about 10-20gigs on my internal for one of the two Linux OSs.


So if I go down this route, and install Ubuntu on the internal, is it (hd0) is (hd1) for where I want to install grub? Or is there an easier solution that I can do right now to install grub rather than trying to figure it out when the only system that works on my PC is the one on the Live CD - read-only in all its glory?

---

### Post by logos34 on 2007-02-12
> I've also made XP bootable again, and I'm back on it right now to write the post. But the fact that MBR works now doesn't seem to have made a difference in starting up Ubuntu.

Clarification: you've made it bootable again by restoring the windows bootloader or does grub now boot it?

---

### Post by Kougaiji on 2007-02-12
> **logos34 said:**
> Clarification: you've made it bootable again by restoring the windows bootloader or does grub now boot it?

windows bootloader

---

### Post by logos34 on 2007-02-12
Ok, here's what I suggest: leave the windows disk as is.  If you can't get ubuntu to boot from usb, by all means try putting it on your other ide.  I hate to keep harping on this, but just unplug the windows disk--you've got it working, no need to risk messing it up again.  Install ubuntu and grub to other drive.  Turn off. Connect your windows drive, reboot.  Go into the bios and make sure Ubuntu (slave) is first in the hard disk boot priority and windows (master) second.  Then post output from 
> sudo fdisk -l 

Then you can edit your menu.lst and fstab.

---

### Post by Kougaiji on 2007-02-12
> **logos34 said:**
> Ok, here's what I suggest: leave the windows disk as is.  If you can't get ubuntu to boot from usb, by all means try putting it on your other ide.  I hate to keep harping on this, but just unplug the windows disk--you've got it working, no need to risk messing it up again.  Install ubuntu and grub to other drive.  Turn off. Connect your windows drive, reboot.  Go into the bios and make sure Ubuntu (slave) is first in the hard disk boot priority and windows (master) second.  Then post output from 


Then you can edit your menu.lst and fstab.

Thanks a **LOT**. I'm very grateful for the help. I'll take your advice and post results hopefully tomorrow. If all goes well, I'll be posting from my first Linux OS ever.

---

### Post by logos34 on 2007-02-13
Before you reinstall, I was thinking you might try the following to get your usb drive to boot: 

Since you said that you used 'hd1' (going by the boot order) and just get a flashing cursor, then apparently hd1 is the second internal drive because grub is seeing the ide disks before the usb: 1. (hd0) ide master (windows), 2. (hd1) ide slave, and 3. (hd2) USB drive.  So try to boot from the second ide and see if that brings up the grub menu...if you're lucky you'll be able to boot the ubuntu kernel on sda1. Then, knowing that usb is hd2, you can setup grub on the usb mbr as follows:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window.
3. Type "sudo grub" 
4. Type "root (hd2,0)", (assuming / is sda1, the first partition)
5. Type "setup (hd2)"
**OR if you want to write it to your / root partition instead of the mbr, then you would type "setup(hd2,0)". 
6. Quit grub by typing "quit".
7. Reboot.

Go into the bios and change it back so it boots from the usb first. Maybe now you'll be able to boot to grub on the mbr (or /) of the usb drive.

---

### Post by Kougaiji on 2007-02-13
Alright, installed just fine on the second internal. Error 22 is gone. I can still boot XP.

Now I'm getting closer to finally booting it. However, I ran into a more common error: error 17. I tried to fix it by typing this in the terminal with the Live CD:
```
sudo grub
root (hd1,1)
setup (hd1)
```

But it still shows the same error. My hard drive is partitioned automatically with the installation tool such that partition #2-#5 are reserved for Ubuntu.

Anything I'm doing wrong?

---

### Post by logos34 on 2007-02-13
> sudo grub
root (hd1,1)
setup (hd1)

If hd1 is hdb, and / is hdb2, then it looks right.  It should go on the mbr.  What's on #3-5 (swap, extended?)

---

### Post by Kougaiji on 2007-02-14
> **logos34 said:**
> If hd1 is hdb, and / is hdb2, then it looks right.  It should go on the mbr.  What's on #3-5 (swap, extended?)

Here is my output from sudo fdisk -l now:
```

Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2491    20008926    c  W95 FAT32 (LBA)

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       17253   138584691    7  HPFS/NTFS
/dev/hdb2   *       17254       19363    16948575   83  Linux
/dev/hdb3           19364       19457      755055    5  Extended
/dev/hdb5           19364       19457      755023+  82  Linux swap / Solaris

```

I don't really understand what I'm doing wrong.

Should I have typed "setup (hd1,1)" instead of just "setup (hd1)"?

---

### Post by logos34 on 2007-02-14
This is from the grub error page:
> error 17 : "Invalid device requested"
This error is returned if a device string is recognizable but does not fall under the other device errors.

Now run the following commands if you could:
 
Then:
> sudo mkdir /ubuntu
sudo mount -t auto /dev/hdb2 /ubuntu
cat /ubuntu/boot/grub/device.map
cat /ubuntu/boot/grub/menu.lst
cat /ubuntu/etc/fstab  [edit]

Copy and post it all.

---

### Post by Kougaiji on 2007-02-14
here you go

```
ubuntu@ubuntu:~$ sudo mkdir /ubuntu
ubuntu@ubuntu:~$ sudo mount -t auto /dev/hdb2 /ubuntu
ubuntu@ubuntu:~$ cat /ubuntu/boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb
ubuntu@ubuntu:~$ cat /ubuntu/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=09b07b3f-b108-4f49-b9a8-ad4efffa942c ro
# kopt_2_6=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
chainloader     +1

ubuntu@ubuntu:~$ cat /ubuntu/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=09b07b3f-b108-4f49-b9a8-ad4efffa942c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=65732f55-cf70-4557-830d-5b85aa04f804 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
ubuntu@ubuntu:~$ 

```

---

### Post by logos34 on 2007-02-14
Your files look just as they should.  Not sure what the problem is.  Grub is on hdb mbr and it points to the kernel on hdb2.  So you're getting the grub menu, and the error message comes back when it tries to boot the default kernel?  What about windows, can you boot to it when you choose it on the grub menu?

---

### Post by Kougaiji on 2007-02-14
> **logos34 said:**
> Your files look just as they should.  Not sure what the problem is.  Grub is on hdb mbr and it points to the kernel on hdb2.  So you're getting the grub menu, and the error message comes back when it tries to boot the default kernel?  What about windows, can you boot to it when you choose it on the grub menu?

No the grub message comes up before I even get to the menu. I have yet to see the grub menu. I'm going to try to do grub setup on (hd1,1) and see if that makes a difference over (hd1).


Maybe I need a bios update? It **is** almost 6 years old now..



Edits:
did setup (hd1,1), seems like it's failing according to output. So I did setup (hd1) again to make sure nothing went wrong.
```
grub> setup (hd1,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,1)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,1) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
```

---

### Post by logos34 on 2007-02-14
> Maybe I need a bios update? It is almost 6 years old now..

That was the very next thing I was going to ask...Does your bios support booting beyond 1024 cylinder limit?

---

### Post by logos34 on 2007-02-14
If it doesn't and you can't update it, you could create a /boot partition just before your ntfs. 

[edit: although you should be covered since most systems since '98 should have a bios that supports that].

---

### Post by logos34 on 2007-02-14
If it's not a bios issue, I'd try using SuperGrub next.  D'load and burn it to a cd or make a floppy.  Follow the instructions at hermanzone.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by logos34 on 2007-02-14
What make and model motherboard do you have?

---

### Post by Kougaiji on 2007-02-14
Well I've updated the bios and that fixed error 17. 2 errors out of the way!

I've gotten to the grub menu on bootup, but when I select any of the Ubuntu options, it give me error 22: could not find partition or something like that. I'm looking into it...


Oh yeah. I remember, while looking for solutions to my last problem, running into a forum thread that had all the common startup errors and what could be causing it. Any idea where I can find something like that because I've been looking, but in all the wrong places it seems.

---

### Post by Kougaiji on 2007-02-15
And this marks my first message from Ubuntu that isn't booted via Live CD!

I managed to fix grub by downloading super grub and now I an boot Ubuntu! It's pretty awesome!

All problems solved.

---

