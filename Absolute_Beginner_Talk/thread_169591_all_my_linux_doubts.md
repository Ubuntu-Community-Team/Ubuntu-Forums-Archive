---
title: "all my linux doubts"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Patok on 2006-05-02
first of all, sorry if my english is not very good, it isnt my first language

i migrated to linux recently doing a dualboot with windows xp and i have many doubts so i will put them all in one thread

1. DUALBOOT: the dualboot didnt work as planned, I first installed windows xp in one partition and then in another one I installed ubuntu. but, in the grub when I restart I can only choose the ubuntu kernel
2.MSN: is there a better choice for messasing that amsn, i find it very buggy.. then I find that GAIM doesn't have enough msn options (i'm looking for msn specially, so i don't care if it comes with aim or icq)
3.IPOD: what's the best ipod software for linux?

thank you

---

### Post by NyTE on 2006-05-02
I know what to do for ipod

Use GTK pod or Yami pod.

---

### Post by catlett on 2006-05-02
I don't use it but it's supposed to do what you want. Hope it helps. [http://www.jabber.org/user/](http://www.jabber.org/user/)

---

### Post by nanotube on 2006-05-03
are you on breezy (5.10) or dapper (6.06). if you are on breezy, then the version of amsn that is available in the default repositories is old. you should install the newest one, that has had a number of bugfixes and features added. maybe that will solve your msn problems.

---

### Post by aysiu on 2006-05-03
If you want the latest version of aMSN on Breezy, go [here](http://www.ubuntuforums.org/showthread.php?p=978766#post978766).

---

### Post by nanotube on 2006-05-03
[QUOTE=aysiu]If you want the latest version of aMSN on Breezy, go [here](http://www.ubuntuforums.org/showthread.php?p=978766#post978766).[/QUOTE]
hehe nice. can always trust aysiu to cook up a shell script to automate stuff. :)

---

### Post by towsonu2003 on 2006-05-03
[QUOTE=Patok]
1. DUALBOOT: the dualboot didnt work as planned, I first installed windows xp in one partition and then in another one I installed ubuntu. but, in the grub when I restart I can only choose the ubuntu kernel[/QUOTE]
brrr... I would be so panicked :)

Open a terminal (hit alt+f2, type gnome-terminal, hit enter for ubuntu. change gnome-terminal to konsole for kubuntu)
can you post (copy paste) the output of 
```

sudo fdisk -l
cat /boot/grub/menu.lst

```
and finally, do you remember whether you wanted grub to go to your MBR (master boot record) during installation?

notes: 
be very careful with fdisk, it's dangerous
try to identify which of the output of fdisk -l is your primary (booting) windows partition, if you have more than one NTFS partitions.

---

### Post by Patok on 2006-05-03
I already had installed the latest amsn still i didnt like it, im going to try again on GAIM

towsonu2003: 
Disk /dev/hda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         542     4097488+   b  W95 FAT32
/dev/hda2   *         543       15305   111608280   83  Linux
/dev/hda3           15306       15505     1512000    5  Extended
/dev/hda5           15306       15505     1511968+  82  Linux swap / Solaris


hda1 is my fat32 windows partition

---

### Post by stansz on 2006-05-03
lol well....i had sorta had the same problem...im liking linux rite now...but when i tried to get back into winodws...it wouldant work....i guess it was because i used a pirated version of it..lol 
but im not very worried...i dont have much stuff on this desktop anyways

btw this is my first post...cheers all

---

### Post by aysiu on 2006-05-03
My Windows partition is /dev/hda1, but it's NTFS (I'm not sure if that makes a difference), as opposed to FAT32: ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by nalmeth on 2006-05-03
Try mercury messenger, that might be better.
Install the latest version of GTKPOD for your ipod

---

### Post by Mustard on 2006-05-03
[QUOTE=aysiu]My Windows partition is /dev/hda1, but it's NTFS (I'm not sure if that makes a difference), as opposed to FAT32: ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```[/QUOTE]

It doesn't matter whether its FAT or NTFS.  The menu.lst entry is the same for both.

---

### Post by aysiu on 2006-05-03
[QUOTE=nalmeth]
Install the latest version of GTKPOD for your ipod[/QUOTE] Is the latest version necessary if you have a slightly older (not Video or Nano) iPod?

Well, if Patok wants the latest version, [here it is](http://ftp.us.debian.org/debian/pool/main/g/gtkpod/gtkpod_0.99.4-1_i386.deb).

---

### Post by towsonu2003 on 2006-05-03
[QUOTE=Patok]I already had installed the latest amsn still i didnt like it, im going to try again on GAIM

towsonu2003: 
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         542     4097488+   b  W95 FAT32
/dev/hda2   *****         543       15305   111608280   83  Linux
/dev/hda3           15306       15505     1512000    5  Extended
/dev/hda5           15306       15505     1511968+  82  Linux swap / Solaris

```

hda1 is my fat32 windows partition[/QUOTE]
so your windows is on a fat32, not ntfs, right? AND you have only one hard disk?

and the output of
```

cat /boot/grub/menu.list
```?

edit: didn't see there was a second page to thread...

---

### Post by Patok on 2006-05-03
only one hardisk yes, and windows is on fat32
when i enter 
> cat /boot/grub/menu.list
i get
> cat /boot/grub/menu.list

I'm on breezy btw

---

### Post by towsonu2003 on 2006-05-03
[QUOTE=Patok]only one hardisk yes, and windows is on fat32
when i enter 
```
cat /boot/grub/menu.list
```
i get
```
cat /boot/grub/menu.list
```

I'm on breezy btw[/QUOTE]
:confused: :confused: :confused: 

am I misspelling the command (am on Windows now)? even if I am, the output shouldn't be that :confused: :confused: :confused:

---

### Post by towsonu2003 on 2006-05-03
misspelled. output of this one
```
cat /boot/grub/menu.lst
```
(no i in list) sorry :oops:

edit: corrected my first post here so others looking for solution here don't get frustrated.

---

### Post by Mustard on 2006-05-03
[QUOTE=towsonu2003]misspelled. output of this one
```
cat /boot/grub/menu.lst
```
(no i in list) sorry :oops:[/QUOTE]
Heh..I didn't notice that one either. Easy mistake to make. :)

---

### Post by Rinzwind on 2006-05-03
If you want you might also be able to use MSN under Ubuntu with WINE.
I think I saw it in my wine programs list when I tried wine :)

---

### Post by Ferri on 2006-05-03
If you don't mind using KDE, I find Kopete quite good. I supports most instant messaging services (including MSN) and in the last KDE version, it also supports webcams.

---

### Post by kostyabkg on 2006-05-03
As a good messenger I suggest QNext from [www.qnext.com](www.qnext.com)

---

### Post by Patok on 2006-05-03
ok, here it is finally

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

--------------------------------------

about msn: i decided to use GAIM finally

---

### Post by Omnios on 2006-05-03
I will second Mercury as a MSN client its the closest thing to a fully functional MSN client with winks and Nudge.

---

### Post by towsonu2003 on 2006-05-03
hmmm, that's weird that grub didn't see your windows OS. That doesn't really happen. May be that's because it's on a fat partition??? 

before doing any of the following, make sure you have an ubuntu live cd (and an install cd) handy :) Check out this link -maybe print? or open on another pc?- in case you (I) get your grub screwed (i.e. if you loose ability to boot): [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

open terminal, and type
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst

```
the first one will make a backup of your menu.lst in case we screw it (you can replace the new one with old old one using the live CD if grub gets confused). 
the second command will open grub menu.lst for you to edit. copy-paste the following (thanks aysiu) to the end of that file. Save and close. Reboot and pray. 
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
You are supposed to see the Windows entry at the end of the boot menu. Highlight it and press enter to boot Windows. Pray some more. 


Side note: there is a chance this will not work because your Windows partition is not flagged for boot. I am absolutely NOT sure. I'm just noting this here, so that someone who knows this might contribute. You fdisk **-l** output was:
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         542     4097488+   b  W95 FAT32
**/dev/hda2   ***         543       15305   111608280   83  Linux
/dev/hda3           15306       15505     1512000    5  Extended
/dev/hda5           15306       15505     1511968+  82  Linux swap / Solaris

```
notice the *, which is the boot flag. 

In my installation, (assume I have the same partitions), fdisk would look like this:
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/hda1   ***           1         542     4097488+   b  W95 FAT32
/dev/hda2             543       15305   111608280   83  Linux
/dev/hda3           15306       15505     1512000    5  Extended
/dev/hda5           15306       15505     1511968+  82  Linux swap / Solaris

```
Again, I am NOT sure... Try the grub thingy first :)

---

### Post by Mustard on 2006-05-03
I think you might have picked it, towsonu2003.

My output for sudo fdisk -l is showing my windows partition marked as active with the boot flag too.

```
mustard@slave:~$ sudo fdisk -l

<snip>

   Device Boot      Start         End      Blocks   Id  System
**/dev/hdb1   *           1        1022     8209183+   c  W95 FAT32 (LBA)**
/dev/hdb2            1023        9729    69938977+   5  Extended
/dev/hdb5            1023        1659     5116671   83  Linux
/dev/hdb6            2298        2934     5116671   83  Linux
/dev/hdb7   *        2935        3572     5124703+  83  Linux
/dev/hdb8            3573        9729    49456071   83  Linux
/dev/hdb9            1660        2297     5124703+  83  Linux

<snip>

```

I don't know whether thats going to prevent grub from working with the above entry you crafted, but it certainly might answer why it didnt recognise the windows partition first time around.

---

### Post by Patok on 2006-05-04
I tried your way towsonu2003

my fdisk now looks like you said it would look

in the grub menu I can choose windows but when i Choose it  it says something like (dont remember exactly

title           Windows
filesystem type is fat (0,b)
savedefault
makeactive
chainloader     +1

then it asks me to insert a boot disk or to press enter so ubuntu boots

----------------------
mercury messenger?looks interesting,  i'm going to try that..

---

### Post by Mustard on 2006-05-04
[QUOTE=Patok]I tried your way towsonu2003

my fdisk now looks like you said it would look

in the grub menu I can choose windows but when i Choose it  it says something like (dont remember exactly

title           Windows
filesystem type is fat (0,b)
savedefault
makeactive
chainloader     +1

then it asks me to insert a boot disk or to press enter so ubuntu boots

----------------------
mercury messenger?looks interesting,  i'm going to try that..[/QUOTE]

Yeah, I would suspect you need to set the boot flag on the windows partition.  I'm not exactly sure of the best way to do it.  The one way I can think of offhand is to use *qtparted*, as I know it has the option to do so.  You could try downloading *qtparted* using synaptic in Ubuntu and then starting that up, loading the partion information on /dev/hda and try right clicking on /dev/hda1 and set the boot flag on.  I assume you can do this without it effecting the data on that partition.

---

### Post by Patok on 2006-05-04
heres my qtparted screen what do i do now?

[IMG]http://img12.imagevenue.com/img.php?loc=loc283&image=20895_Screenshot.jpg[/IMG]

---

### Post by towsonu2003 on 2006-05-04
[QUOTE=Mustard]Yeah, I would suspect you need to set the boot flag on the windows partition.  I'm not exactly sure of the best way to do it.[/QUOTE]
I think s/he did set the boot flag:
[QUOTE=Patok]
my fdisk now looks like you said it would look
[/QUOTE]
am I correct?

ok, so... I googled to see if grub has known problems with fat32 (no); we set the boot flag as it looks in my machine; we put the lines I and aysiu have for /dev/hda1 Windows to menu.lst. This is supposed to work now :confused: 

I would now try various ways described in the wiki: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

Read it once fully without doing anything, so you know what's going on and what's to be done... my favorite way is:
1. Make backup of /boot/grub/menu.lst
2. Boot from install CD Rescue Mode
3. Mount all partitions
4. ```
grub-install /dev/hda
```
5. check /path/to/boot/grub/menu.lst for errors. 
6. reboot and pray...

---

