---
title: "Annoying dual-boot grub problem"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by henryhund on 2006-06-11
I have (what I think is) an interesting problem with dual booting XP and Ubuntu with GRUB.  Last week I installed Ubuntu for the first time and allowed the LiveCD to partition my single harddrive for me.  I ran across this problem, so I manually partitioned the drive and I have XP on the first partition.

So here's the problem:  When I boot up I run into a hanging GRUB_ or GRUB _ (got the space in between there after manually editing the partition table).  I can boot into Windows or Linux using the LiveCD and selecting boot from first hard drive, which takes me to the GRUB menu.  This leads me to believe GRUB is working and there is one trivial issue holding it back from working on a normal boot.

I have the latest bios for my motherboard, as per suggested by the official GRUB guide.

Thanks for your help in advance.

---

### Post by henryhund on 2006-06-12
I don't usually like to do this, but...

bump.

---

### Post by catlett on 2006-06-12
Well lets check your partitions and then check your grub menu and make sure all the labels are right. Go to the terminal and enter this for a list of your partitions```
 sudo fdisk -l
``` Thehn enter this to open your grub list in a text editor ```
sudo gedit /boot/grub/menu.lst
``` Copy/paste them in a reply.

---

### Post by henryhund on 2006-06-12
Thanks catlett:

```

sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7060    56709418+   7  HPFS/NTFS
/dev/hda2            7188        9716    20314192+  83  Linux
/dev/hda3            7061        7187     1020127+   5  Extended
/dev/hda4            9717        9729      104422+  83  Linux
/dev/hda5            7061        7187     1020096   82  Linux swap / Solaris
/dev/hda6            7061        7061           0+  83  Linux

Partition table entries are not in disk order
henry@henry-laptop:~$[CODE]
```
[/CODE]

```

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
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by catlett on 2006-06-12
Your entries in the menu are fine. Grub uses 0 as a value so /dev.hda1 to grub is hd0,0.
As you can see from fdisk windows is /dev/hda1 and grub has windows as (hd0,0), which is correct. Grub has ubuntu at (hd0,1), which also matches fdisk's output /dev/hda2.
There are 2 things you can do that will hopefully solve the problem. One is to update grub. The other is to reinstall grub. With ant luck grub will rewrite itself and the error will be overwritten. Other than that, I don't know what to suggest. The entries match your partitions, it should boot.```
 sudo update-grub
``` If that doesn't work, try reinstallimg grub with```
 sudo grub-install /dev/hda
``` Try one and then the other and post if your still getting errors.

---

### Post by henryhund on 2006-06-12
Catlett,

thanks for your help.  My issue isn't resolved.  I got no errors when running those commands.  Could it be my system just wasn't made for linux?  (I have another error, with DVDs, I was planning on starting another topic about after resolving this one.)

---

### Post by catlett on 2006-06-13
I don't know why iy isn't working. For the heck of it. What type of hard drive do you have? Is it ide or sata? I ask because lately there are alot of issues with grub and sata.
There is another option but I never installed it after install. lilo . lilo is the original linux bootloader (it's name is from[COLOR="Red"] li[/COLOR]nux [COLOR="Red"]lo[/COLOR]ader Here is synaptic package manager's description
> LInux LOader - The Classic OS loader can load Linux and others
This Package contains lilo (the installer) and boot-record-images to
install Linux, OS/2, DOS and generic Boot Sectors of other OSes.

You can use LILO to manage your Master Boot Record (with a simple text screen,
text menu or colorful splash graphics) or call LILO from other Boot-Loaders to
jump-start the Linux kernel. This might work better than grub in your case. The only thing is I haven't installed lilo after install. The times I had it, it came with the install as the default bootloader.
I would googlr it or seasrch the ubuntu wiki to find more info on replacing grub with lilo.

Sorry I couldn't be of more help.


P.S. To run DVD's in linux you have to install quite a few codecs and playback applications. If you are a little use to the command line, this is what I follow when I set up ubuntu from scratch [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

### Post by DougC on 2006-06-13
Hi,

When you get the Brub boot menu move to the windows entry or linux entry and press e to edit the entry.

Check every line to make sure its ok.
ie root   (hd 0,0)
chainloader +1 etc

It should look similar to the menu.lst in the /boot.

If the entries are not the same as the menu.lst then post back here.

---

### Post by henryhund on 2006-06-13
Doug and catlett, thanks for your help.  I'll post here with the information requested after work.

By the way each entry works if I select it after using "boot to first hard disk" from the live cd.

---

### Post by catlett on 2006-06-13
[QUOTE=henryhund]Doug and catlett, thanks for your help.  I'll post here with the information requested after work.

By the way each entry works if I select it after using "boot to first hard disk" from the live cd.[/QUOTE]
That's strange. Try update grub or grub install. Actually this time run it as```
 sudo grub-install (hd0,0)
``` It's strange that it loads from the live cd but not normally. I wonder why?
Just in case, go into your bios menu and see what the boot order is. Maybe there is something there.
You only have one hard drive so I don;'t know why it doesn't boot like it does from the live cd. The live cd boot means grub is installed and working. The problem is the boot process without the live cd. I don't understand how the boot process is different from the "boot from hard drive" in the live cd and a normal boot from the hard drive on setup.

Keep posting errors. Every time you post the thread gets back to the front page, hop4efully someone will see it that has a solution.

---

### Post by henryhund on 2006-06-13
Catlett-  I am confused by that as well.  Logically, if GRUB works after selecting the hard disk from the live cd, it should work on its own.  Will having a CD listed as the first boot in BIOS cause issues with Ubuntu?  I mean, the times I'm trying to boot with GRUB on its own I have no disc in the tray.

My disk is IDE.  It is an internal disk, as I have a laptop.

I will post all the other information requested when I get home, as I am very late for work.

---

### Post by catlett on 2006-06-13
The only thing I see that isn't right is the lack of an ignore symbol on your grub menu list. I don't think it will make a difference but at this point I wouldn't pass on anything. So put a # where I put them and try that. I don't think it is affecting anything but it is incorrect to have those two lines uncommented.
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
[COLOR="Red"] title		Other operating systems:
root[/COLOR]
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
[COLOR="Red"]# title		Other operating systems:
# root[/COLOR]

---

### Post by henryhund on 2006-06-13
I did as you commanded and unfortunately, it did not help.  I'm going to do now as doug suggested.  I'll post my results shortly.

---

### Post by henryhund on 2006-06-13
[QUOTE=DougC]Hi,

When you get the Brub boot menu move to the windows entry or linux entry and press e to edit the entry.

Check every line to make sure its ok.
ie root   (hd 0,0)
chainloader +1 etc

It should look similar to the menu.lst in the /boot.

If the entries are not the same as the menu.lst then post back here.[/QUOTE]

I checked and re-checked all this info and it is all identical.  :-( 

What is the deal here?  :confused:

---

### Post by confused57 on 2006-06-13
Your problem sure is a puzzler, I don't know anything about laptops; but was wondering if you went into your bios, and turn off any IDE controllers that don't have anything connected to them.

I guess if all else fails, you could boot up with the Windows install CD, fixmbr, and reinstall Ubuntu.

What does your fstab file show?:
```
cat /etc/fstab
```

Good luck...

---

### Post by henryhund on 2006-06-13
[QUOTE=confused57]Your problem sure is a puzzler, I don't know anything about laptops; but was wondering if you went into your bios, and turn off any IDE controllers that don't have anything connected to them.

I guess if all else fails, you could boot up with the Windows install CD, fixmbr, and reinstall Ubuntu.

What does your fstab file show?:
```
cat /etc/fstab
```

Good luck...[/QUOTE]

Here's my fstab...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Thanks for your help everyone.  I really hope I can fix this.  **Can I reinstall the MBR and somehow boot Ubuntu from the Windows NTLDR?  If that would be easier I'd just as soon forget GRUB.**

---

### Post by drtvasudevan on 2006-06-13
[QUOTE=henryhund]Catlett-  I am confused by that as well.  Logically, if GRUB works after selecting the hard disk from the live cd, it should work on its own.  Will having a CD listed as the first boot in BIOS cause issues with Ubuntu?  I mean, the times I'm trying to boot with GRUB on its own I have no disc in the tray.

I will post all the other information requested when I get home, as I am very late for work.[/QUOTE]

you have not posted the bios settings.
first boot device i assume is cdrom
is second first hard disk?

alternatively you can install xosl as i do and configure it. easy, no brainer. you can install from windows. but before that you must install grub in linux's own partition for that to work.

---

### Post by henryhund on 2006-06-13
CDROM is first, Hard Drive is second.  I switched it with no effect.  Trying to find a way to rewrite the MBR without a floppy.

---

### Post by drtvasudevan on 2006-06-14
suggest you install grub in the linux patition itself first.
second install xosl.
it will reconfigure and write the mbr for you.
tv

---

### Post by Soarer on 2006-06-14
It may not be the same problem, but I tried to get GRUB working on my Compaq evo with no joy. Did pretty much all of the things you have. It would boot from Live CD but just hung on GRUB when booting from the hard disk. I think that the installation process wasn't overwriting the MBR, but I'm not sure.

So, as advised, I went to LILO and it pretty much worked first time. Only time since it failed was when GRUB was updated in pre-release Dapper.

---

### Post by DougC on 2006-06-14
You can use the NTLDR, I've done this myself before and it works fine.

Look here for info:

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

Doug.

---

