---
title: "Grub Error 17 / Dual boot w/ XP"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Nutopia on 2008-01-19
Hello,

I'm in the right place - I'm very new with this. I installed ubuntu yesterday successfully on a new computer I just got. That one has windows xp and ubuntu running happily together.

So then since I like ubuntu and it worked easily enough, I figured I'd try it on my older pc - still retaining windows but wanting to use ubuntu. this pc has 2 hdds, an 80gb with xp and no partitions and a slave 250gb. I did the same thing for this older pc as i did on the new one, only difference is I wanted to put Ubuntu on my slave drive. I partitioned off a nice chunk of space and the install seemed to work. However, after I rebooted I got the now seemingly legendary 'Grub Error 17'

I'm not good with linux at all and can't really do anything (yet.) I did investigate the issue and try to fix on my own but I don't quite get what I'm doing, which is where you come in!
I'm going to be around all day, so if anyone wants to help me out I would appreciate it. I can't get to windows or ubuntu on this machine (although I'm using it now off of the boot CD, which - incidentally - is not corrupt)

Here is info on the drives (I noticed in previous posts this is always asked for, so I'm jumping the gun - I try to be a good student ;)):

```
Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe25de25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156344579    78172258+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb1919bda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   357992459   178996198+   c  W95 FAT32 (LBA)
/dev/sdb2   *   357992460   482351624    62179582+  83  Linux
/dev/sdb3       482351625   488392064     3020220    5  Extended
/dev/sdb5       485371908   488392064     1510078+  82  Linux swap / Solaris
/dev/sdb6       482351751   485371844     1510047   82  Linux swap / Solaris
```

Thanks in advance!

---

### Post by acormack on 2008-01-19
What does your /boot/grub/menu.lst contain?

---

### Post by Nutopia on 2008-01-19
I'm not sure how to determine that :confused:

What command do I use?

---

### Post by acormack on 2008-01-19
cat /boot/grub/menu.lst

---

### Post by Nutopia on 2008-01-19
cat /boot/grub/menu.lst
returns
cat: /boot/grub/menu.lst: No such file or directory

I'm running off of the boot CD... is there another way I can find this file? I dont have a grub directory under boot at alll.

(I'm sorry for being so noob... If anyone wants to IM: SMS8484 on AIM)

---

### Post by logos34 on 2008-01-19
root needs to be mounted.  click on it in places>computer

---

### Post by acormack on 2008-01-19
Try opening a terminal window

then 

mkdir /tmp/ubdrive

then

sudo mount /dev/sdb2 /tmp/ubdrive

then

cd /tmp/ubdrive/boot/grub

then

cat menu.lst

---

### Post by Nutopia on 2008-01-19
You guys :guitar:

ubuntu@ubuntu:/tmp/ubdrive/boot/grub$ cat menu.lst
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
# kopt=root=UUID=ce5f50b3-e358-43c9-bcc5-be55a2478a52 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ce5f50b3-e358-43c9-bcc5-be55a2478a52 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ce5f50b3-e358-43c9-bcc5-be55a2478a52 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
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
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by acormack on 2008-01-19
try 

cat /tmp/ubdrive/boot/grub/device.map

---

### Post by Nutopia on 2008-01-19
(hd0)   /dev/sda
(hd1)   /dev/sdb

---

### Post by Nutopia on 2008-01-19
if it can't be fixed, can someone help me get my machine to boot back into windows?

---

### Post by logos34 on 2008-01-19
If nnoe of the [suggestions here]("http://users.bigpond.net.au/hermanzone/p15.htm#17") work, get out your windows install cd, boot into recovery console and run 

**fixmbr **

at the prompt.  It will restore the windows bootloader to the mbr of sda.

Or you can use the Super Grub Disk.

You could try [writing grub to the mbr of sdb from the ubuntu live cd]("http://ubuntuforums.org/showthread.php?t=224351"), then switching the Bios boot order so sdb boots first.  You'd have to edit ubuntu entries in menu.lst to 'root (hd0,1)' and change the windows entry so that it [looks like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

### Post by isparkes on 2008-01-19
Well, Grub Error 17 means that grub is trying to boot from the wrong hard disk. This happens because the "root" given to grub is wrong. You should be able to sort this out "interavtively":

Here's the important bits from this post: [https://answers.launchpad.net/ubuntu/+source/grub/+question/14606](https://answers.launchpad.net/ubuntu/+source/grub/+question/14606)

At the grub menu, press 'e' and check the "root (hd0,2)" or similar line. You can go into command mode with 'c' and use the 'find' command to locate the right partition, for instance: find /boot/grub/menu.lst

Once you have found the right (hdx,y) partition, edit the root line in the grub menu. After booting up, edit the #groot= line in /boot/grub/menu.lst and run 'sudo update-grub'.

---

### Post by isparkes on 2008-01-19
Don't despair - this absolutely is solvable.

---

### Post by acormack on 2008-01-19
I am confused also.  

Are you saying it doesn't boot into Windows or Ubuntu?

Do you get the same error message if you select either?

---

### Post by logos34 on 2008-01-19
> **isparkes said:**
> Well, Grub Error 17 means that grub is trying to boot from the wrong hard disk. This happens because the "root" given to grub is wrong. You should be able to sort this out "interavtively"...

You need to read post #1,8,10.  He's booting from sda, which is what menu.lst and device.map have down--they're correct.

---

### Post by Nutopia on 2008-01-19
Sorry for the delay... I had some stuff to do...

Anyway - thanks to everyone trying to help! I really want to get this figured out.

1. Nothing boots - when I restart the PC all I get is the Grub error. I have no choice to do anything except enter BIOS

2. I bought this PC in 2002 and I don't know where my original discs are - odds are they are in the basement of my parents house which is where I'm not at right now. I really dont want to give up - I'd like to get this working - but if it can't get fixed, does anyone know what I can do without my original boot discs? I have the most up to date version of XP on this machine.

3. I'm basically confused now and I apologize. Fun fact: I'm a software engineer (also i'm only 24) and I'm really good at what I do, but unfortunately it's not this. Basically, I do LAMP, and my weak part is the L - so I want to get good at it. I should probably go back and take some classes but until then all I have is you folks!


So far, my understanding is that GRUB, which is is the boot loader, is not finding ubuntu, which is on my second hard disk drive (hd1) on the second partition (1) - so it should be pointing at :  root (hd1,1). It looks like the menu.lst file is pointing there, as logos34 has stated.

Unfortunately, that leaves me about where I started. Unless my summary above is wrong...(hopefully). 

If there is anyone out there that can help I'm back and ready to go...

---

### Post by logos34 on 2008-01-19
> **Nutopia said:**
> 2. I bought this PC in 2002 and I don't know where my original discs are - odds are they are in the basement of my parents house which is where I'm not at right now. I really dont want to give up - I'd like to get this working - but if it can't get fixed, does anyone know what I can do without my original boot discs? I have the most up to date version of XP on this machine.

As I stated above,
> 
Or you can use the Super Grub Disk.

Find a way to download it (~50 MB) and burn it to CD.  

You could also download a copy of a [win98 floppy boot disk]("http://www.bootdisk.com/bootdisk.htm") (-->win98 SE OEM) and run

**fdisk /mbr**

Or, again (from post above), 
> You could try writing grub to the mbr of sdb from the ubuntu live cd, then switching the Bios boot order so sdb boots first. You'd have to edit ubuntu entries in menu.lst to 'root (hd0,1)' and change the windows entry so that it looks like this.

---

### Post by Nutopia on 2008-01-19
> You could try writing grub to the mbr of sdb from the ubuntu live cd, then switching the Bios boot order so sdb boots first. You'd have to edit ubuntu entries in menu.lst to 'root (hd0,1)' and change the windows entry so that it looks like this.



yes. this is where i'm confused. i dont know what the acronym sdb is. even if i did i'm not sure i could do what it is you're describing without more directions how to do it.

---

### Post by capink on 2008-01-19
You can try reinstalling grub form the live cd.

First, make sure that your root is mounted (follow the steps on post 7)

Second, run the following command:

```
sudo grub-install --root-directory=/tmp/ubdrive '(hd0)'
```


Edit: If you want to write grub to the mbr of the second disk as the above post suggested. The command would be

```
sudo grub-install --root-directory=/tmp/ubdrive '(hd1)'
```

---

### Post by logos34 on 2008-01-19
> **Nutopia said:**
> yes. this is where i'm confused. i dont know what the acronym sdb is. even if i did i'm not sure i could do what it is you're describing without more directions how to do it.

sdb is your linux drive! (see the fdisk you posted page 1).  I gave you the instructions and even the link for how to install grub from the live cd in post #10 above!  

Or use the 'grub-install' method capink just provided. either way.

good luck.

---

### Post by Nutopia on 2008-01-19
unfortunately re-installing grub from the last post doesn't seem to have worked.

---

### Post by Nutopia on 2008-01-20
thanks for everyone's help. i was able to find a windows cd and i just fixed the mbr. i'm going to enjoy ubuntu on my computer for awhile and play with it there. then i'm going to splurge on a new hard drive to back things up onto, wipe everything out on my old pc and try again. probably the best course of action in the long run.

hey - at least i got it working on one machine!

---

### Post by kukibird1 on 2008-01-20
If you decide to try again with the same setup  after install boot into your bios setup screen  and set both
your hard drives to on or auto save  changes and reboot . I had this same problem it worked for me .

---

### Post by narehart on 2008-02-06
I've had this problem before follow the directions in this  [post]("http://ubuntuforums.org/showthread.php?t=498395").

---

### Post by ar2000jp on 2008-02-06
I had this problem, and I solved it, it's because of BIOS limitations.
I've read the solution from another post, but I don't remember where it was.

Older hardware (Like my MB, it's Soltek nForce 2, from around 2004) can't boot from partitions further than 8GB from the start of the disk.

To solve this, I created a small /boot partition (around 60 MB) in the beginning of the HDD, created my NTFS partitions, then my Linux / and swap.

If you don't know how to install Linux correctly on these partitions, ask around the forums.

Note: The NTFS partitions might not work very well, unless you do a full format on them in Windows.

Sorry for the quick post :)

---

### Post by dstew on 2008-02-06
The other possibility is that the file system on the Linux partition was corrupt, and therefore could not be mounted. It would have been good for the OP to do fsck on that partition.

---

