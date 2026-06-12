---
title: "Dual-Boot Problem"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by mechz on 2008-04-13
I followed this guide to install a dual boot.
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Its a little outdated, I installed version 7.10

Anyway Ubuntu installed fine, and Ive been using it, but when trying to boot into XP it seems to get stuck at "Starting up..." it just stays there, instead of running a disc check on it self as the guide sugests might happen.

Any idea as to what went wrong? Possible solutions? The only step I skipped was "Configure GRUB" but in the tutorial that comes after xp is veryfied working, and aslo, seems optional. Thanks for any advice.

---

### Post by Martje_001 on 2008-04-13
Can you post your **/boot/grub/menu.lst** here (in code-tags)? And the output of **fdisk -l** in a terminal?

---

### Post by mechz on 2008-04-13
> **Martje_001 said:**
> Can you post your **/boot/grub/menu.lst** here (in code-tags)? And the output of **fdisk -l** in a terminal?

Are there instructions on this forum, on how to execute those two tasks? I ot a little ambitious witht he dual boot, but this my first time using linux.Thanks, in the mean time I'll google.

---

### Post by Michael.Godawski on 2008-04-13
To display the content of the boot/grub/menu.lst file run this in terminal

```
cat /boot/grub/menu.lst 
```

The other commands would be
```

sudo fdisk -l
```

The terminal is in Applications > Accessories > Terminal

---

### Post by mechz on 2008-04-13
```
centurion@centurion-desktop:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=bf4101d4-5a2a-4870-859e-3d9d16dcac66 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=bf4101d4-5a2a-4870-859e-3d9d16dcac66 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=bf4101d4-5a2a-4870-859e-3d9d16dcac66 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

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
makeactive
chainloader     +1

centurion@centurion-desktop:~$ 


```

```
Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb872b872

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3294    26459023+   7  HPFS/NTFS
/dev/hda2            3295        4791    12024652+  83  Linux
/dev/hda3            4792        4863      578340    5  Extended
/dev/hda5            4792        4863      578308+  82  Linux swap / Solaris
```

hope i did that right.

---

### Post by TeoBigusGeekus on 2008-04-13
Type 
```
sudo gedit /boot/grub/menu.lst
```
in a terminal.

Delete the line that say's "savedefault" in the winxp title. Save the file and reboot.
Try that to see what happens...

---

### Post by mechz on 2008-04-13
will do.

---

### Post by unutbu on 2008-04-13
According to
[http://www.softwaretipsandtricks.com/forum/windows-xp/34338-windows-stuck-start-up.html](http://www.softwaretipsandtricks.com/forum/windows-xp/34338-windows-stuck-start-up.html)
the solution seems to be to boot from the XP CD. Choose Repair, get to the Recovery Console, and do

```
chkdsk /r
```

You also have an opportunity to see if Ubuntu can fix your Windows:
Boot Ubuntu. Open a terminal.

```
sudo /sbin/dosfsck /dev/hda1
```

If that works, please report. It's sure to warm the cockles of a few Linux-loving hearts.

---

### Post by mechz on 2008-04-13
Typing this from the secondary computer. XP still seems to be stuck on "Starting Up..."

Give it a few minutes?

Edit: Roget that unut, I'll give it a go.

---

### Post by bumanie on 2008-04-13
It might be that your windows mbr is corrupted. You could repair windows mbr, but then you would have to reinstall grub via the ubuntu live cd. Not hard to do, but the whole process is a bit of mucking around. Up to you whether you want to try this or try other suggestions first.

---

### Post by lswest on 2008-04-13
i had the same problem (my computer has 2 drives though) and i solved it by adding **map (hd0) (hd1)** and **map (hd1) (hd0)** after the root line for the Windows entry.  Try adding **map (hd0)** after the root line.

---

### Post by mechz on 2008-04-13
> **lswest said:**
> i had the same problem (my computer has 2 drives though) and i solved it by adding **map (hd0) (hd1)** and **map (hd1) (hd0)** after the root line for the Windows entry.  Try adding **map (hd0)** after the root line.

menu.lst now comes up blank, after doing TeoBigusGeekus suggestion, unless Im doing something wrong.

---

### Post by mechz on 2008-04-13
> **unutbu said:**
> According to
[http://www.softwaretipsandtricks.com/forum/windows-xp/34338-windows-stuck-start-up.html](http://www.softwaretipsandtricks.com/forum/windows-xp/34338-windows-stuck-start-up.html)
the solution seems to be to boot from the XP CD. Choose Repair, get to the Recovery Console, and do

```
chkdsk /r
```

You also have an opportunity to see if Ubuntu can fix your Windows:
Boot Ubuntu. Open a terminal.

```
sudo /sbin/dosfsck /dev/hda1
```

If that works, please report. It's sure to warm the cockles of a few Linux-loving hearts.

I tried the xp disc suggestion, but I didnt set an admin password when I installed Xp, and now its asking for it, would leaving it blank work?

Your other suggestion gives me this

```
Tdosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 0.

```

---

### Post by mechz on 2008-04-13
> **bumanie said:**
> It might be that your windows mbr is corrupted. You could repair windows mbr, but then you would have to reinstall grub via the ubuntu live cd. Not hard to do, but the whole process is a bit of mucking around. Up to you whether you want to try this or try other suggestions first.

I believe theres a dual boot tutorial that outlines this in my bookmarks somewhere.If these fixes dont work though, I think a clean XP install is what I'll be doing.

My linux excursion sure was...interesting. :popcorn:

---

### Post by unutbu on 2008-04-13
> I tried the xp disc suggestion, but I didnt set an admin password when I installed Xp, and now its asking for it, would leaving it blank work?

Did you try leaving it blank?

Before you re-install XP, you might want to try Super Grub ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)). It is the best boot rescue disk that I know of. Among other things, it has an option to boot windows directly. There is information on how to burn and use it here: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

Note that if you re-install Windows, it will overwrite the MBR and Ubuntu will no longer load. That's okay if you wish to return to the Windows world exclusively, but if you wish to have a dual-boot system, you'll need to re-install a bootloader such as GRUB. If you go with GRUB, and Windows boots but Linux doesn't, I'd again suggest trying the SuperGrub disk as a handy tool.

---

### Post by mechz on 2008-04-13
> **unutbu said:**
> Did you try leaving it blank?

Before you re-install XP, you might want to try Super Grub ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)). It is the best boot rescue disk that I know of. Among other things, it has an option to boot windows directly. There is information on how to burn and use it here: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

Note that if you re-install Windows, it will overwrite the MBR and Ubuntu will no longer load. That's okay if you wish to return to the Windows world exclusively, but if you wish to have a dual-boot system, you'll need to re-install a bootloader such as GRUB. If you go with GRUB, and Windows boots but Linux doesn't, I'd again suggest trying the SuperGrub disk as a handy tool.

Thanks for all the help.Yeah leaving it balnk worked and it said it repaired one or more errors, buit nothing changed.It still seemed to get stuck at starting up.Thanks for the info on that tool. I think I'll reinstall both xp and ubuntu later, I think I might have accidentally messed up my ubuntu install trying all these solutions.You have a dual boot, yeah? Can I ask, what route did you go, or would recommend, linux first or windows first? Thanks.

---

### Post by unutbu on 2008-04-13
Actually, I used to dual boot, but for the past few years have gone to pure Linux systems. 

If you want to create a dual-boot system, however, you should install Windows first. 
The problem is that Windows assumes there are no other operating systems in the world, so it overwrites the MBR with the expectation that its files will be on the first partition of the first hard drive. To satisfy windows, the easiest way is to install Windows first so it ends up where it expects. Then you install Linux on a different partition, and overwrite the MBR with GRUB, which is much more flexible about handling multiple operating systems.

---

### Post by bumanie on 2008-04-13
If you wish to reinstall both OSes, it is best to reinstall via this method (my opinion)
1. Install windows as per normal
2.Get a program such as the gparted live cd and partition your drive by shrinking windows and formating a portion to ext3 with it.
3. Install ubuntu onto ext3 partition, but at the partitioning stage it would be advantageous to set up a minimum 6g / a 1-2g swap and the add a separate /home as large as you like/have room for. To do this you need to choose 'manual' at the partitioning stage
The advantage of this is that if the File system of ubuntu becomes corrupted somehow, you only have to reinstall / and the saved data in /home will be safe.
If you don't want to go through a full reinstall, you could try fixing windows mbr and then reinstall ubuntu as above so that if the file system gets wrecked or you have problems like you've had this time, you should only have to reinstall to / to fix things.
To fix windows mbr, go into recovery console. Choose/type 1, supply username and password if asked (in your case no password) and then type fixboot --> enter fixmbr --> enter --> quit/reboot/exit (can't remember windows preferred command, sorry). By playing around with grub and ubuntu, you should not have destroyed your windows partition, unless you partitioned incorrectly. At least if windows works again, it saves you some time by only having to reinstall ubuntu. As stated, it is a good idea to have a separate /home partition.
Hope it all works in the end. I always count these annoying set backs as learning experiences.

---

### Post by TeoBigusGeekus on 2008-04-13
> **mechz said:**
> menu.lst now comes up blank, after doing TeoBigusGeekus suggestion, unless Im doing something wrong.
I'm sorry about that, I was just trying to help...

---

### Post by Martje_001 on 2008-04-13
Try playing with the following lines in **/boot/grub/menu.lst** (you can edit it by typing **gksudo "gedit /boot/grub/menu.lst"** in a terminal)
```
title           Microsoft Windows XP Home Edition
root            (hd0,0)

```
Change it to```
title           Microsoft Windows XP Home Edition
root            (hd0,1)

```
and, if that doesn't work
```
title           Microsoft Windows XP Home Edition
root            (hd0,2)

```
etc.

---

### Post by Herman on 2008-04-19
If you are getting as far as a blue screen with the words 'starting up', it means that GRUB has already done what it is supposed to do correctly and most likely you have a problem of some kind within Windows itself.

A useful boot CD for Windows which contains the three vital boot loader files for Windows XP, (ntldr, NTDETECT.COM and a specially edited version of boot.ini can be found at the following website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm").
If you use that CD to try to boot Windows, it will by-pass the hard disk's MBR, Windows' boot sector, ntldr, NTDETECT.COM and boot.ini, so if you had a problem with any of those Windows should boot up from that CD.

There's no such thing as a 'Windows MBR', and 'fixing' the MBR would only be useful if your MBR has been corrupted by a virus in Windows and you had already cleaned the virus.
The best way to 'fix' the MBR is to install GRUB to it, which you had already done.
So called 'boot sector' viruses can install malicious code in either the MBR or the Windows boot sector, and install virus code somewhere else where the Windows user can't detect it, such as in the first track of the hard disk or in blank sectors after the end of the Windows partition. By altering the boot sector or MBR, they cause Windows to load via the virus, so the virus loads before Windows loads, so it has complete control of your computer, and, also, Windows won't boot if the virus is removed. That's because the MBR or more likely the boot sector are pointing to the virus code and not directly to the Windows boot-up files like they're supposed to.

Since you already installed GRUB to MBR, running 'FIXBOOT' like bumanie said may help, that restores the Windows boot sector, which is indeed the first sector of the Windows partition, and without which Windows can't normally boot.
(As opposed to the MBR, which can have any boot loader installed in it, and Windows will still boot up just fine).

Another useful command you can apply from a Windows Recovery Console is 'bootcfg /rebuild', which will generate a brand new boot.ini file if none exists, or fix a corrupted boot.ini file for you.

After that, another problem you can have in Windows is a corrupted file system, which CHKDSK /R should have fixed already for you. Sometimes it helps to run that two or even three times.

One trick that is sometimes useful with Windows is to try pressing your F8 key when it's booting to see if you can get a menu from where you can select 'safe mode'.[ Safe Mode]("http://en.wikipedia.org/wiki/Safe_mode")  - wikipedia.
That might work or maybe not, but it's worth a try. I have had success booting Windows in safe mode when it refused to boot normally due to a well known brand of antivirus meddling with the video settings and drivers.

I realize this thread is a week old, but maybe some of this advice will still help somebody, if not the original poster, possibly someone else searching for answers here.

Regards, Herman :)

---

