---
title: "Screwed up my MBR for windows!"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by HoLLyw00dGT on 2008-02-26
OK, already had XP, installed Ubuntu 7.10. Start my computer, prompted to choose linux general or whatever or windows XP pro. 

I choose linux...it opens up just fine...

I choose XP pro and i get = Starting . . .

and nothing...

From what I am reading i screwed up my MBR because GRUB overwrote it or something. IDK what to do now. I have been trying to find answers without deleting all of my partitions and reinstalling. Anyone...plz? 

Thanks, 
-SuperF**KING newbie

---

### Post by JoshuaRL on 2008-02-26
Just as a question, did you defrag XP and backup before installing?

One option is to try reinstalling XP'x MBR, and then reinstalling Grub so you can get to both.

Load a recovery disk for XP and go into the Recovery Console.  Try:
```

fixmbr
fixboot

```
Then go get the [SuperGrub Live CD](http://supergrub.forjamari.linex.org/) and reinstall Grub.  That should fix it.

---

### Post by HoLLyw00dGT on 2008-02-26
I defragged before i installed ubuntu today, something i didn't do the other day. I used xpressrecovery2 on my mobo to restore windows last night.(backedup on xpressrecovery when i built myc omp 3 weeks ago)  Yes i already screwed up once. I didn't back up before installing TODAY because everything was fresh. Some more newbie questions. My xp rescue cd? idk what that is lol, i mean i have the xp cds. Is the cd i used to install xp the rescue cd? Also where do i go to fix mbr adn type those commands.

---

### Post by JoshuaRL on 2008-02-26
Yes, the CDs you use to install XP.  When you boot into that CD, it should have an option to press something and go to the Recovery Console.  It should either be ESC or one of the F-keys.

---

### Post by northern lights on 2008-02-26
If the problem still persists:

Could you also post the outputs of ```
cat /boot/grub/menu.lst
``` and ```
sudo fdisk -l
```
(that's fdisk -"lower case L")

You're bootmenu entry for Windows might simply be wrong.

---

### Post by HoLLyw00dGT on 2008-02-26
I put in my windows xp cd, only think that it give sme options is f6 or f2, f2 is automated system recovery...i hit that, then it asks for the recovery FLOPPY disk. I dont have one. I'm beginning to think i'm **** out of luck. I will run those codes in my terminal but i'm pretty sure it is the MBR issue rather than an order issue...like i understand them anyway >_< lol. 

I burned the supergrub iso image liek stated above, but i can't use that until my windows recovery thing is figured out right?

---

### Post by HoLLyw00dGT on 2008-02-26
Here are my results for typing the first code in terminal:

ustin@justin-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=781cf1a7-42c2-44c2-8712-5c1e6b47a60f ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=781cf1a7-42c2-44c2-8712-5c1e6b47a60f ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=781cf1a7-42c2-44c2-8712-5c1e6b47a60f ro single
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
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


Here are my results for the second command:

justin@justin-desktop:~$ sudo fdisk -l
[sudo] password for justin:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13359   107306136    7  HPFS/NTFS
/dev/sda2           13360       37700   195519082+  83  Linux
/dev/sda3           37701       38456     6072570    5  Extended
/dev/sda4           38457       38897     3538944   de  Dell Utility
/dev/sda5           37701       38456     6072538+  82  Linux swap / Solaris
justin@justin-desktop:~$

---

### Post by northern lights on 2008-02-26
Darn, that's indeed not it.

Maybe this [forum post]("http://ubuntuforums.org/archive/index.php/t-24113.html") might help.

---

### Post by HoLLyw00dGT on 2008-02-27
Alright. Ran windows rescue, and fixmbr and fixboot. Success! Now running superergrub cd, following instructions but having trouble understanding. All you said was reinstall grub. Not sure on the grub disk how I do that.

"If you want to recover your linux boot OR if you want grub back into your MBR you should choose:

Option: GNU/Linux
Option: Fix boot of linux (grub)

Which one? or any at all? Thx again guys for bearing with my linux affluency /sarcasm

***Another EDIT*** Ok so i went on with the cd and i am presented with menus. now what

---

### Post by JoshuaRL on 2008-02-27
Alright, lets use the Ubuntu Live CD instead to install Grub

Can you post the output of:
```

sudo fdisk -l

```
You'll need to run that from the LiveCD terminal.

---

### Post by northern lights on 2008-02-27
He already did:
> **HoLLyw00dGT said:**
> justin@justin-desktop:~$ sudo fdisk -l
[sudo] password for justin:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13359   107306136    7  HPFS/NTFS
/dev/sda2           13360       37700   195519082+  83  Linux
/dev/sda3           37701       38456     6072570    5  Extended
/dev/sda4           38457       38897     3538944   de  Dell Utility
/dev/sda5           37701       38456     6072538+  82  Linux swap / Solaris
justin@justin-desktop:~$

Could```
grub
root hd(0,0)
setup (hd0)
```do the trick?

---

### Post by JoshuaRL on 2008-02-27
> **northern lights said:**
> He already did:


Could```
grub
root hd(0,0)
setup (hd0)
```do the trick?

That was what I was gonna try next.  Sorry I missed the fdisk.

---

### Post by HoLLyw00dGT on 2008-02-27
Boot from HDD...disc read error. Restoring my system back to clean again. You know, its a good damn thing its easy to restore and doesnt hurt anything cuz the past few days havn't been good for me and my PC lol. Now to just finally find a writeup i can understand that I won't have this problem again. How do I NOT **** up the MBR? BTW guys, thank you so much for your help. Quick responses, knowledgable help. I appreciate it now and DEF in the future lol

-Justin

---

### Post by JoshuaRL on 2008-02-27
Well, if you're wiping the drive and starting fresh I would suggest installing XP first, then use the Guided - Partition choice from the Installation of Ubuntu.  Just use the slider to make the size of the Ubuntu partition.  It should be really simple.

---

### Post by HoLLyw00dGT on 2008-02-27
That is exactly what i did before. The slider bar is the size of the Ubuntu partition you say? thats what i assumed so thats good. I read guided was easiest so thats what i did. What is screwing my MBR?

---

### Post by JoshuaRL on 2008-02-27
Not sure, it shouldn't have any problems.  Does it give errors this time?

---

### Post by HoLLyw00dGT on 2008-02-27
Idk, doing a partition scan on the live cd to make sure everything was cleared except my xp. Idk either man, my mbr gets screwed everytime. i did a scan, 

/dev/sda1 - NTFS 278.55gig...boot flag
unallocated - unallocated 16gig
/dev/sda4 - ext2 3.38gig
unallocated - unallocated 127.51mb

have xp installed, no ubuntu yet, just did a partition scan.

Those partitions mean anything to you?

-Justin

---

### Post by northern lights on 2008-02-27
sda1 is your Windows partition, sda4 some linux remainder (you're about to do a fresh Ubuntu install, right?!), that, especially if it can't hold any substantial data, you should erase. You should also install onto the ext3 filesystem

If you were to see a graphical interface, it would probably look like this:

| Windows/279 | unallocated space/16 | ext2/3.4 | unallocated/128 |

After deleting the ext2, it should be:

| Windows/279 | unallocated/148 |

and then you either make it

| Windows/279 | Ubuntu/ext3/147 | swap/1 |

or, for instance, anything along the lines of

| Windows/279 | Ubuntu/ext3/20 | swap/1 | ... | ... | or how many ever more partitions you feel like having for data storage (NTFS is read by both OSs) |

---

### Post by Zorael on 2008-03-08
For future reference, if you want to restore the "standard" MBR to a disk and you don't have an XP installation cd at hand, you can install **testdisk** from the official repositories, either from a working (K/X/Ed)ubuntu installation or from a Live CD of such.

```
[ MBR Code ]  Write TestDisk MBR code to first sector
```
Choose that, should work.

And before you bust out your torch and pitchforks to burn me as the piratebayer that I am, my XP copy is legitimate, but it came preinstalled on my laptop with only a service partition to **reinstall** XP.

---

