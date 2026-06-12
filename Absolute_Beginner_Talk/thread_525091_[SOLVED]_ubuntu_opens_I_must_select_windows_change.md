---
title: "[SOLVED] ubuntu opens I must select windows change"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by sluggo1234 on 2007-08-13
Grub automatically opens Ubuntu and if I am quick I can chose the Windows OS to open.  I would like to change that so Grup will open windows if do not quickly select ubunto.     I work with windows most often so I need it to automatically open to the windows OS with a chance to select Ubuntu if I want to practice and learn more about Ubuntu
sliuggo1234

---

### Post by meierfra on 2007-08-13
You will need to edit the file /boot/grub/menu.lst

 open a terminal (Applications->Accessorie->Terminal)

and type

```
gedit /boot/grub/menu.lst
```

Post the output  and we will be  able to tell  you exactly how to edit the file.

---

### Post by meierfra on 2007-08-14
You can also follow these instructions:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_Operating_System_boot-up_for_GRUB_menu]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_Operating_System_boot-up_for_GRUB_menu")

---

### Post by sluggo1234 on 2007-08-14
Meierfra
I am really new to Ubuntu. First mistake I downloaded Kubuntu and it took over Ubuntu, I thought that I would have a choice of which one to use but I guess not. After Ubuntu opens and I enter the username and password Kubuntu opens. The terminal in Kubuntu seems to be different to the terminal I had learned to use and was getting pretty good using in Ubuntu. I need to remove Kubuntu so only Ubuntu will open then I can try the code:
gedit /boot/grub/menu.lst 
So far I cannot get it to work in Kubuntu
Thanks
slluggo1234

There are no stupid questions, however they are easier to answer.

---

### Post by meierfra on 2007-08-14
Seems you really overwrote Ubuntu, otherwise "gedit" would work. Do this instead:


```
kate /boot/grub/menu.lst
```

---

### Post by sluggo1234 on 2007-08-15
Meierfra,
This code works but the left column (pane) top says menu.1st and the right column(pane) large is blank with a blue line across the top.  Perhaps I asked the question wrong. I have a KDE desktop, which in itself is OK, but I want to go back to my GNOME desktop. But I may have overwritten and it may be gone. Hope not as it was easier for me to use. 
sluggo

---

### Post by p_quarles on 2007-08-15
It's menu.lst, not menu.1st (lower case L, not One)

---

### Post by amazingtaters on 2007-08-15
I'm not for sure on this, but can't you get the ubuntu GNOME desktop via

sudo apt-get install ubuntu-desktop

---

### Post by meierfra on 2007-08-15
Both of the two previous  post are correct.

But before installing "ubuntu-desktop" we should figure out what   really happened to your  previous version of ubuntu.  Maybe it  is on  different partition. Post the output of

```
sudo fdisk -l
```

( again l is a lower case L)

---

### Post by sluggo1234 on 2007-08-15
Meierfra,
Here is what you asked for first. I will come back with the answer to <sudo fdisk -l > after this post.
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
# kopt=root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by sluggo1234 on 2007-08-15
Disk /dev/hda: 81.9 GB, 81964302336 bytes
240 heads, 63 sectors/track, 10587 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4112    31086688+   c  W95 FAT32 (LBA)
/dev/hda2            4113       10387    47439000   83  Linux
/dev/hda3           10388       10587     1512000    5  Extended
/dev/hda5           10388       10587     1511968+  82  Linux swap / Solaris
sluggo@Linux-desktop:~$

---

### Post by meierfra on 2007-08-15
Ubuntu seems to be gone but let's worry about that later.

To  automatically boot  windows to this:

( To avoid typos use "copy and paste" rather than retyping.)

Switch to the /boot/grub directory:

```
cd /boot/grub
```

Backup the file menu.lst

```
sudo cp menu.lst menu.lst.backup
```

open the file:

```
sudo kate  menu.lst
```

(You need "sudo"  to be able to change the file)

Look for the end of the second paragraph and change

default  0

to

default  5

Save the file. Next time you boot, it should   boot into windows.

(To explain the "5":  Grub starts counting at 0 and  "windows" is the sixth  entry in your  grub boot up menu,)

---

### Post by sluggo1234 on 2007-08-15
sluggo@Linux-desktop:~$ cd /boot/grub
sluggo@Linux-desktop:/boot/grub$ cp menu.lst.backup
cp: missing destination file operand after `menu.lst.backup'
Try `cp --help' for more information.
sluggo@Linux-desktop:/boot/grub$

---

### Post by p_quarles on 2007-08-15
Try cutting and pasting the line that meierfra gave you (and notice how it's different from what you typed). You'll have better luck that way.

---

### Post by sluggo1234 on 2007-08-15
When I enter cp menu.lst menu.lst.backup I get the following:
bash: menu.lst: command not found
:confused:

---

### Post by meierfra on 2007-08-15
Oops,  there should have been a "sudo" in front of that command. I fixed it in the original post.
Although you should have gotten a different error message, so I'm not sure whether something else went wrong. I double checked all my lines of codes.  (I tried them all out myself with  "copy and paste")  So you really shouldn't have any more problems.

---

### Post by sluggo1234 on 2007-08-15
The reason that I was retyping instead of cut and paste was because the forum is on one computer and Ubuntu is on another.  Now I have several windows open on the computer with Ubuntu and I will be able to cut and paste now. It was easier to use the switch between computers than try to find my way back and forth. In Window ME when I hit the box with the minus sign-upper right corner, I can find the tab at the bottom of the page and bring it back up. Here they seem to disappear and where they go I don't have a clue as yet.  But I think this is right; kate may be wrong as I am now in GNOME and not KDE.

sluggo@Linux-desktop:~$ cd /boot/grub
sluggo@Linux-desktop:/boot/grub$ sudo cp menu.lst menu.lst.backup
Password:
sluggo@Linux-desktop:/boot/grub$ sudo kate menu.lst
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Following this another window opened and here is what it had in it:
the left pane had menu.lst in it and the following is the right pane:

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
# kopt=root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by meierfra on 2007-08-15
You are confusing me:

Did you try to edit the file /boot/grub/menu.lst?


> 
am now in GNOME and not KDE.
Do you have two computers: one  running ubuntu and the other kubunu?  Or did you reinstall ubuntu-desktop? 

And which computer do you want to t  automatically  boot into  windows


> . In Window ME when I hit the box with the minus sign-upper right corner, I can find the tab at the bottom of the page and bring it back up.

It should be the same in Gnome and Kubuntu. (again something that needs to be fixed sometime later)

---

### Post by sluggo1234 on 2007-08-15
Meierfra wrote:
You are confusing me:

Did you try to edit the file /boot/grub/menu.lst?


Quote:
am now in GNOME and not KDE.
Do you have two computers: one running ubuntu and the other kubunu? Or did you reinstall ubuntu-desktop?

And which computer do you want to t automatically boot into windows


Quote:
. In Window ME when I hit the box with the minus sign-upper right corner, I can find the tab at the bottom of the page and bring it back up.
It should be the same in Gnome and Kubuntu. (again something that needs to be fixed sometime later)


One computer runs XP pro other has Windows ME and Ubuntu+Kubuntu. But I found out how to get back to GNOME and I am no longer in KDE.  Actually as far as I could tell there is no menu.lst  I tried the edit and then tried to open it. This shows all of that if you read down through it as follows this is what I did and you can see the result. 

sluggo@Linux-desktop:~$ cd /boot/grub
sluggo@Linux-desktop:/boot/grub$ sudo cp menu.lst menu.lst.backup
Password:
sluggo@Linux-desktop:/boot/grub$ sudo kate menu.lst

Then this came up;
X Error: BadDevice, invalid or uninitialized input device 167
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device

Following this in a few seconds a large window opened with two panes side by side
On the left at the top only this menu.lst .
Then the right pane had this in it and I have no idea what it means.
But here it is:

 menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=4da2a7e5-dd40-41b4-9838-cc3124c1e5f8 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows 95/98/Me
root (hd0,0)
savedefault
makeactive
chainloader +1
__________________

You think your confused wish you were here looking at what I am looking at. I am confused and was confused from the get go.  And since i have to get up at 6AM in the morning and it is 10PM here now, I am hitting the sack. Will come back  tomorrow PM to check out what you think. From 7 until 12 or 1PM  I will be under going a heart test at the heart clinic here.  
Sluggo1234:lolflag:

---

### Post by jw5801 on 2007-08-15
Ignore those "X device" errors that you're getting, everyone gets those so it's ok. The text editor still ran and is showing the exact same file you posted here the first time!
Find where it says this:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0
``` and change it to this ```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default 5[/COLOR]
```

On another note you should probably use "gksudo" (graphical sudo) instead of sudo to open a graphical app. Using sudo on graphical applications can sometimes mess with permissions.

To get your window list back, right click on a panel (you should have one at the top with an applications menu and one at the bottom but you may have deleted the one at the bottom) and go add to panel, then find "Window List" and add one of those. You now should see all the open windows!

Finally just to make posts with big long text files in them easier to read the forums have code tags that you can use! Just put [ code]*text to be put in code tags!*[/code ] and it should come out like this: ```
*text to be put in code tags!*
```
NB: I've put an extra space in each of my code tags above so that you can see what the tag is meant to look like, don't include or it won't work!

Hope the heart test all went ok!

EDIT: and to alleviate your concern that the command line is different in Kubuntu as opposed to Ubuntu, it's not. The only difference is the graphical interface, Kubuntu used KDE as opposed to Ubuntu's Gnome. All the bash commands are exactly the same, the reason your gedit command didn't work is because gedit is the default text editor for Gnome, so it won't be there in Kubuntu, unless you install it. kate is the equivalent KDE text editor.

---

### Post by meierfra on 2007-08-15
> 10PM here now, I am hitting the sack. 

Good night!

> I will be under going a heart test at the heart clinic here. 

Good Luck!


> But I found out how to get back to GNOME and I am no longer in KDE.

Good!

> Actually as far as I could tell there is no menu.lst   ...
Then the right pane had this in it and I have no idea what it means.

The right pane is the file "menu.lst". That is the file you need to change.

> But here it is:

menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

See  the "default 0" ?

That needs to be  changed to "default 5".

Since your already backed the file up, and you are now using gnome just do this:

```
gksudo gedit  /boot/grub/menu.lst 
```

A window will pop up ( And since you are now using gedit you   will just have one pane)
Look for "default   0"  and change it  to "default  5".
Save the file and reboot.

---

### Post by p_quarles on 2007-08-15
To reduce the risk of damaging your system, please use this instead:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by meierfra on 2007-08-15
> So reduce the risk of damaging your system, please use this instead

gksudo gedit /boot/grub/menu.lst

Sorry, I keep forgetting. I changed my post.

---

### Post by sluggo1234 on 2007-08-16
It  worked great. I appreciate the hard work all of you did in helping this newbie.  I feel like I will eventually learn my way around. It has been several years since I had Mandrake 9.0 and an instructor from "Down Under" to help me learn how to use it a little.  I worked with it off and on for about a year. Then I was doing web pages more hours a day than I want to remember. Windows is so much faster for me at least that I gradually let Mandrake go. Now it is no longer Mandrake but close to the same thing I imagine.

I said then "that if they got a GUI that worked like Windows Linux would take off". So many things are so much better  in Linux.  But now I am working with digital images and restoring old photos for people. Photoshop is great, but when CS3 came along they were guided in its build for the first time, I believe, by bean counters instead of photographers and I do not like it.  I am still working with PS 7.0.1.  That takes Windows and I really need XP Pro and lots of memory for that. Gimp is coming along but it is hard to beat PS.  That keeps me on Windows a lot of the time. ME is used to store a lot of images, so if I lose one hard drive I still have two to go.  Yes the second hard drive w2k pro.  And I store  many on it. 
Sluggo1234 :guitar:

However, I had a lot of space on the older ME drive and had heard good things about Ubuntu.  And it is good. Thanks again everyone and especially Zee.
Sluggo1234

---

### Post by Arthur Archnix on 2007-08-16
> On another note you should probably use "gksudo" (graphical sudo) instead of sudo to open a graphical app. Using sudo on graphical applications can sometimes mess with permissions.

What?

---

### Post by p_quarles on 2007-08-16
> **Arthur Archnix said:**
> What?
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by Arthur Archnix on 2007-08-16
> **p_quarles said:**
> [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Huh. Thanks for the link.

---

