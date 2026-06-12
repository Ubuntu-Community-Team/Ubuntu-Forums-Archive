---
title: "XP, Vista, and Ubuntu Multi-Booting Problem"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by flameshad0w on 2007-12-29
Hello, I used to have XP and Ubuntu on dual boot, and then I switched to Vista and Ubuntu on dual boot. After using Vista for a while I felt I'd like to have both Vista and XP along with Ubuntu.
I have two harddrives, and Vista and Ubuntu were on separate ones. 

I tried to shrink the Ubuntu partition to make space for XP and somehow ended up deleting it (no worries, got files backed up). I installed XP, and then reinstalled Ubuntu.

Now I have a Grub Boot Loading screen that let's me choose between XP and Ubuntu, but not Vista. I wanted to add Vista to my menu.lst, but I don't know what its root is. It says Ubuntu's root is (hd1, 1) and XP's root is (hd0, 0).
How could I check what the root of the Vista install is? :confused:

---

### Post by jas0 on 2007-12-29
Please give us the following things:

```
cat /boot/grub/menu.lst
cat /boot/grub/device.map
sudo fdisk -l
```

This will help us see what your current partition setup is and what you need to add for Vista.

---

### Post by flameshad0w on 2007-12-29
menu.lst
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
# kopt=root=UUID=ec00d0f8-1a7a-4b9a-bd4a-33fe2b86a4af ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ec00d0f8-1a7a-4b9a-bd4a-33fe2b86a4af ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ec00d0f8-1a7a-4b9a-bd4a-33fe2b86a4af ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title           Windows XP Professional Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

device.map
```
(hd0)   /dev/sda
(hd1)   /dev/sdb
```

fdisk
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244195008+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           18183       19456    10233373+   7  HPFS/NTFS
/dev/sdb2               1       13738   110350453+  83  Linux
/dev/sdb3           13739       14230     3951990   82  Linux swap / Solaris
/dev/sdb4           14231       18182    31744440    b  W95 FAT32

Partition table entries are not in disk order
```

---

### Post by meindian523 on 2007-12-29
You have installed Vista to your 160 GB HDD,correct?

If yes,you need to add this to the end of your menu.lst file:
```

title           Windows Vista
root            (hd1,0)
savedefault
makeactive
chainloader     +2
```

---

### Post by flameshad0w on 2007-12-29
No, Ubuntu and XP are both installed on the 160gig harddrive while Vista is installed on the 250gig one. 

When I add what you wrote to the boot menu, I get to a black screen which says "Starting up..." and nothing happens. I don't know if this is the startup screen for Vista or not.

Could this have anything to do with the fact that prior to installing XP on the 160gig harddrive, I tried shrinking the Vista partition to install it there, changed my mind, and then enlarged it again? After doing this I had successfully logged onto Vista so I didn't think there were any problems, but now I'm not sure.

---

### Post by meierfra on 2007-12-29
The problem is that you installed XP after Vista. XP does not recognize Vista and overwrote the boot information for Vista ( You are able to boot XP  from (hd0,0).But (hd0,0)   is the Vista partition)

I  really don't know how to fix this.

You could try this: Use the Vista CD to fix the Vista boot sector.
Physically remove the Vista Drive and then fix the Windows boot sector.

But there should be better ways to fix your problem.

---

### Post by flameshad0w on 2007-12-30
Thanks, I repaired the Vista boot sector using my Vista DVD. It broke the XP one but that's ok for now. I tried all the possible roots for XP and none seem to work, so I'm guessing it's impossible to use Grub to boot up two different Windows versions? I might have to use Vista's own boot loader to switch between the specific versions after choosing Windows in the Grub menu if that's the case...

---

### Post by jas0 on 2007-12-30
> **flameshad0w said:**
> Thanks, I repaired the Vista boot sector using my Vista DVD. It broke the XP one but that's ok for now. I tried all the possible roots for XP and none seem to work, so I'm guessing it's impossible to use Grub to boot up two different Windows versions? I might have to use Vista's own boot loader to switch between the specific versions after choosing Windows in the Grub menu if that's the case...

If nothing else, that would be a pretty interesting setup. I'm pretty sure that you can use GRUB for that though. I remember seeing one of my friends' machines having the same setup using GRUB. I'll ask him about how he did it tomorrow if the issue hasn't been resolved by then.

For now, you can keep trying differrent menu.lst configurations if you're interested.

---

### Post by chuchan on 2007-12-30
> **flameshad0w said:**
> Thanks, I repaired the Vista boot sector using my Vista DVD. It broke the XP one but that's ok for now. I tried all the possible roots for XP and none seem to work, so I'm guessing it's impossible to use Grub to boot up two different Windows versions? I might have to use Vista's own boot loader to switch between the specific versions after choosing Windows in the Grub menu if that's the case...

Hi flameshad0w even i faced the same problem, but after multiple tries and googling i found the proper way to do it. 

1. Install Xp first 
2. Install Vista (Vista can detect Xp's boot sector, this was vice versa till vista, the latest version should be installed first. MS have overcome this problem in vista and enabled it to detect all MS os partitions)
3. Now install ubuntu (in ubuntu grub you will have an entry for Vista and the vista's boot option will have an entry for XP)

thus all three works..... Enjoy!!!!

---

### Post by meierfra on 2007-12-30
You do not have  a grub problem. It is a plain Windows/Vista problem. Windows puts all  boot information into one partition. Fixing the Vista boot destroyed  the boot information  for XP.. You can try my suggestion from my previous post  to fix the XP.

You can also follows the suggestion from the previous post and reinstall XP and Vista. But you will have to change the boot order so that the XP  drive is first. But please do not reinstall Ubuntu. You just need to reinstall Grub. (since  reinstalling Vista will have erased Grub)

---

### Post by meierfra on 2007-12-30
> now, you can keep trying differrent menu.lst configurations if you're interested.

This will not  lead to anything. Grub loads XP by chainloading. That is,  it just looks to the Windows partitions for the booting information.  But the XP booting information has been destroyed  by Vista..

---

### Post by fmartinez on 2007-12-30
> **flameshad0w said:**
> Hello, I used to have XP and Ubuntu on dual boot, and then I switched to Vista and Ubuntu on dual boot. After using Vista for a while I felt I'd like to have both Vista and XP along with Ubuntu.
I have two harddrives, and Vista and Ubuntu were on separate ones. 

I tried to shrink the Ubuntu partition to make space for XP and somehow ended up deleting it (no worries, got files backed up). I installed XP, and then reinstalled Ubuntu.

Now I have a Grub Boot Loading screen that let's me choose between XP and Ubuntu, but not Vista. I wanted to add Vista to my menu.lst, but I don't know what its root is. It says Ubuntu's root is (hd1, 1) and XP's root is (hd0, 0).
How could I check what the root of the Vista install is? :confused:

I've seen a lot of threads about dual boots with Window's Vista, Xp, Fedora, Ubuntu.....etc. You should read up on Easybcd [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) this is a 3rd party boot manager. I've heard of nothing but good things from this boot loader (especially with Vista). I have a dual boot with Vista and Ubuntu using Grub, so I don't know personally but it maybe an option to look into.

---

### Post by flameshad0w on 2007-12-30
> Hi flameshad0w even i faced the same problem, but after multiple tries and googling i found the proper way to do it.

1. Install Xp first
2. Install Vista (Vista can detect Xp's boot sector, this was vice versa till vista, the latest version should be installed first. MS have overcome this problem in vista and enabled it to detect all MS os partitions)
3. Now install ubuntu (in ubuntu grub you will have an entry for Vista and the vista's boot option will have an entry for XP)

thus all three works..... Enjoy!!!!
That's the same thing as I said, first I'd have to choose Vista in Grub and then choose XP or Vista in Vista's boot screen. I managed to do that without reinstalling though, just needed to enable the Vista boot loader and add stuff to it. I was just making sure there wasn't a way to do it all with just Grub alone because that would be slightly better.

> **fmartinez said:**
> I've seen a lot of threads about dual boots with Window's Vista, Xp, Fedora, Ubuntu.....etc. You should read up on Easybcd [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) this is a 3rd party boot manager. I've heard of nothing but good things from this boot loader (especially with Vista). I have a dual boot with Vista and Ubuntu using Grub, so I don't know personally but it maybe an option to look into.
Doesn't EasyBCD just edit Vista's built-in boot loader? That's what I used to get the thing I said above, with one bootscreen to choose Ubuntu or Windows, and then a second to choose XP or Vista if Windows is chosen.
Thanks guys, I'll probably end up doing the two boot screens then.

---

### Post by meierfra on 2007-12-30
You can add Ubuntu to the EasyBCD menu. EasyBCD will load the Grub menu But if you use "hiddenmenu" and "timeout 1" you won't even notice the Grub menu.

---

### Post by meierfra on 2007-12-30
> just needed to enable the Vista boot loader and add stuff to

Can you add XP to the Vista boot loader if you installed XP after Vista?
I didn't know that. Sorry, I thought the whole time that you have no way to boot XP.

---

### Post by chuchan on 2007-12-30
> **flameshad0w said:**
> That's the same thing as I said, first I'd have to choose Vista in Grub and then choose XP or Vista in Vista's boot screen. I managed to do that without reinstalling though, just needed to enable the Vista boot loader and add stuff to it. I was just making sure there wasn't a way to do it all with just Grub alone because that would be slightly better.

Thats is not possible i think, even if you have 3 Windows Operating systems you will have only one boot loader(MBR).....

---

### Post by chuchan on 2007-12-30
Hey i got a work around, but it talks about configuring the Vista boot loader for xp and ubuntu
[URL="http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/"]
http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/ [/URL]

---

### Post by meierfra on 2007-12-30
I just googled it. One can indeed add XP to the Vista boot loader, even if XP is installed after Vista.

[http://hubpages.com/hub/Adding_Windows_XP_to_Vista]("http://hubpages.com/hub/Adding_Windows_XP_to_Vista")


So the "XP before Visa" rule is just as stupid as the "Windows before Ubuntu" rule. It is slightly more convenient to install XP before Vista, but it is insane to reinstall Vista just to obey this rule,

---

### Post by meierfra on 2007-12-30
chuchan:  Your link is broken,

---

### Post by chuchan on 2007-12-30
> **meierfra said:**
> chuchan:  Your link is broken,

Sorry!

Here is the link

[http://duggmirror.com/software/How_to_Build_Triple_Boot_XP_Vista_Ubuntu_with_single_Boot_Screen_wpics/]("http://duggmirror.com/software/How_to_Build_Triple_Boot_XP_Vista_Ubuntu_with_single_Boot_Screen_wpics/")

---

### Post by meierfra on 2007-12-30
> but it talks about configuring the Vista boot loader for xp and ubuntu

[http://duggmirror.com/software/How_to_Build_Triple_Boot_XP_Vista_Ubuntu_with_single_Boot_Screen_wpics/]("http://duggmirror.com/software/How_to_Build_Triple_Boot_XP_Vista_Ubuntu_with_single_Boot_Screen_wpics/")

EasyBCD uses the same method, but does half of the work for you. In particular, if    you use EasyBCD  you won't have to  mess  with the "dd" command (dd can wipe you hard drive if you don't pay attention)

---

### Post by meindian523 on 2007-12-30
And actually,EasyBCD uses Grub,only it makes configuration easier.

If your problem is gone,please consider marking the thread solved.

---

### Post by wasing on 2008-01-01
i just googled your problem and found this link 

[http://lifehacker.com/software/top/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php]("http://lifehacker.com/software/top/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php")

dont know if it will be any help but it looks useful.

also i heard somewere (no sure it might be a rumor but i heard it from an IT guy) that there is actually xp inside vista and you can switch between xp and vista by using like CTRL+?+?

the ? marks are the unknown keys sorry i forgot what he said wasn't plannin on upgrading to vista on my xp machine till it had a stable service pack released..

BTW in my opinion not that anyone cares here but vista is a bunch of DRM and resource hog garbage just covered in a good looking GUI (IDK i like the GUI thats what beryls for though)

---

