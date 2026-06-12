---
title: "Can't boot XP since i installed Ubuntu"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by chrismcollins on 2007-04-12
Hello everyone
I just installed Ubuntu and I'm loving it so far. Ideally I would want to have a dual boot with Ubuntu + Windows XP, but after installing Ubuntu I can no longer boot Windows, after i choose it in GRUB it just says "Disk Error Press Ctrl+alt+delete to restart"... I have Ubuntu 6.10 running on a Toshiba Satellite Laptop. 
Is it possible for me to recover my old windows, or am i screwed?

---

### Post by bashologist on 2007-04-12
> **chrismcollins said:**
> Is it possible for me to recover my old windows, or am i screwed?

Not likely; microsoft's known for screwing their customers. Most people are lucky if they get recovery disks that don't work from the company.

It was a trap; you're with us now and there's nothing you can do. n_n

---

### Post by NICU on 2007-04-12
Hi Chris, can you give a little more information about your installation?  Did you install Ubuntu on a disk that already had XP, or the other way around?  How did you partition your drive?  What version of Ubuntu are you using?

---

### Post by bcmiller on 2007-04-12
> **chrismcollins said:**
> Hello everyone
I just installed Ubuntu and I'm loving it so far. Ideally I would want to have a dual boot with Ubuntu + Windows XP, but after installing Ubuntu I can no longer boot Windows, after i choose it in GRUB it just says "Disk Error Press Ctrl+alt+delete to restart"... I have Ubuntu 6.10 running on a Toshiba Satellite Laptop. 
Is it possible for me to recover my old windows, or am i screwed?

Did you resize the windows partition and then install Ubuntu to the new partition?  Did you then choose to include Windows in grub?

If you have the windows install disk you can try to restore the windows bootloader to the MBR.  That will let you boot soley into Windows if your windows install is intact.  From there you can retry Grub from the livecd or add ubuntu to the boot.ini in windows.

edit: oops what he said ^^^

---

### Post by chrismcollins on 2007-04-12
wow you guys are fast haha thanks!
Um I'll do my best to answer your questions, yes I installed Ubuntu 6.10 onto space I got by resizing the windows partition. I didn't notice anything about including windows in grub :( , I partitioned the drive with 5 gigs for the Ubuntu root, 500 swap, and 10 gigs for /home if that makes sense. I was able to mount the windows drive and access the files, so I think that it's still there... Sorry if that's a little jumbled haha

---

### Post by george29 on 2007-04-12
can you still login too ubuntu? if so open a terminal and post up the output of 

```

sudo fdisk -l
cat /boot/grub/menu.list
df

```

---

### Post by chrismcollins on 2007-04-12
Oh yeah Ubuntu still works fine, just #$#% windows isn't booting at all,

chris@chris-laptop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3442    27647833+   7  HPFS/NTFS
/dev/hda2            3443        3952     4096575   83  Linux
/dev/hda3            3953        4016      514080   82  Linux swap / Solaris
/dev/hda4            4017        4864     6811560   83  Linux
chris@chris-laptop:~$ cat /boot/grub/menu.list
cat: /boot/grub/menu.list: No such file or directory

If i entered the second part of that wrong let me know... Thanks again :)

---

### Post by bashologist on 2007-04-12
> **chrismcollins said:**
> If i entered the second part of that wrong let me know... Thanks again :)

sudo cat /boot/grub/menu.list
# Then paste the contents into [http://www.rafb.net/paste/](http://www.rafb.net/paste/) or a code tag maybe.

---

### Post by george29 on 2007-04-12
hmm try 

```

gedit /boot/grub/menu.list

```

---

### Post by chrismcollins on 2007-04-12
This is what it gave me: 

1chris@chris-laptop:~$ sudo cat /boot/grub/menu.list
2cat: /boot/grub/menu.list: No such file or directory

the gedit just gave me a blank document

---

### Post by bashologist on 2007-04-12
> **chrismcollins said:**
> This is what it gave me: 

1chris@chris-laptop:~$ sudo cat /boot/grub/menu.list
2cat: /boot/grub/menu.list: No such file or directory

the gedit just gave me a blank document

george29 had the wrong spelling. I just copy and pasted his; that's my excuse. Try this:
```
gksudo gedit /boot/grub/menu.lst || gksudo kate /boot/grub/menu.lst
```

---

### Post by chrismcollins on 2007-04-12
Ok that worked a lot better thanks :)

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
default		0
 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
 
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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=2ca1e477-62e4-493f-9801-67b8b3f298dc ro
# kopt_2_6=root=/dev/hda2 ro
 
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
 
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
 
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot
 
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
 
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot
 
title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot
 
### END DEBIAN AUTOMAGIC KERNELS LIST
 
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
 
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by george29 on 2007-04-12
sorry about the spelling...

your menu.lst looks fine - so i'm not sure why you can't boot into windows.

If you can mount the partitions via ubuntu - i'd recommend that you back up all the files that are are on your windows and ubuntu partitions to DVD or an external drive.

then check out this webpage
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by chrismcollins on 2007-04-12
Thanks george29, I appreciate it a lot!

---

### Post by chrismcollins on 2007-04-12
Ok I tried to reboot into windows but i got "a disk read error occured. Press ctr+alt+delete to restart"
Anyone know? I don't want ot give up if there's still a chance...

---

### Post by chrismcollins on 2007-04-12
Ok i tried all the stuff on Super Grub CD now neither windows not Ubuntu will boot from startup, I managed to bood Ubuntu through the Grub disk. How can I get at least Ubuntu to boot from startup again? I'm still hoping to get windows back too though, is there a diagnostic I could run to get Grub installed properly again at least though? thanks:confused:

---

### Post by ciscosurfer on 2007-04-12
> **chrismcollins said:**
> Ok i tried all the stuff on Super Grub CD now neither windows not Ubuntu will boot from startup, I managed to bood Ubuntu through the Grub disk. How can I get at least Ubuntu to boot from startup again? I'm still hoping to get windows back too though, is there a diagnostic I could run to get Grub installed properly again at least though? thanks:confused:If you can boot to a LiveCD of your choice (Ubuntu LiveCD for example) and you can also backup to an external drive, I would recommend backing up your important files before trying these techniques (just to be on the safe side).

You can try fixing your MBR via the Recovery Console (via an XP boot disk or your installation disk).  Here are some links to help you out:
[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)
[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)
[http://www.ntfs.com/mbr-damaged.htm](http://www.ntfs.com/mbr-damaged.htm)
[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)
[http://www.sysint.no/Nedlasting/MbrFix.htm](http://www.sysint.no/Nedlasting/MbrFix.htm)
From Microsoft: [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)
(Hopefully these links will lead you in the right direction)

Then, once that's taken care of, you can reset GRUB to your MBR via these commands: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by chrismcollins on 2007-04-12
Ok first of all sorry to bug you guys again, and thanks for all the help!
Just a quick update, the Super Grub disc fixed my ubuntu boot, and now the message when I try to boot windows has changed to "NTLDR is missing" Does that give anyone a flash? If not I&#314;l start going through all those links ciscosurfer gave me, thanks again everyone!

---

### Post by Bert Mariën on 2007-04-12
If you want to boot back into your WindowsXp system and you do not mind to not being able to boot your Ubuntu, you can restall your windows MBR very easily.

To do so, you only need a bootable  DOS floppy (Win95, Win98...) and boot from there.
Than type:

fdisk /mbr

and you're back in Windows on your next boot (without the floppy of course).

Don't have a floppy drive? Than you'll need to find a bootable cd to do so.

Anyhow, this will give you access to your Windows files again. You can figure out later how to go about the Ubuntu installation.

---

### Post by mattthecat627 on 2007-04-12
Hi, this happened with my laptop when I first installed Ubuntu. After I freaked out for a while because I thought Windows deleted itself, I did manage to find the cause. Go into GParted (install in Synaptic) and click on your Windows partition. In the Partition menu, click "manage flags." Make sure the boot check box is set, and also make sure the partition is not hidden. Hope this works! After I did this it booted up with no problems.

_Matt

---

