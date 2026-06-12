---
title: "[SOLVED] no ubuntu partition?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Bethrine on 2007-08-21
why don't I have a /root ? I had Vista installed and there is no ntfs? I'm trying to get grub to dual boot at startup. HELP!

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             53044356   2433212  47916644   5% /
varrun                  254096        80    254016   1% /var/run
varlock                 254096         4    254092   1% /var/lock
udev                    254096       128    253968   1% /dev
devshm                  254096         0    254096   0% /dev/shm
lrm                     254096     18856    235240   8% /lib/modules/2.6.15-28-386/volatile

---

### Post by dewcansam on 2007-08-21
Don't really understand the whole "why don't I have a /root" question. As, i am almost certain that you in fact do have a /root/ dir. 
$ls -la /root/

>  I'm trying to get grub to dual boot at startup. HELP!
try this [post]("http://ubuntuforums.org/showthread.php?t=423928&highlight=RT2500")
edit /boot/grub/menu.lst and try adding the lines for your particular partition and os

please list your drive configuration to be of better help

---

### Post by Bethrine on 2007-08-21
how do I ask the terminal for my drive configuration? fond a list of roots with that command...

cathy@Bethrine:~$ ls -la /root/
total 44
drwxr-xr-x  7 root root 4096 2007-08-20 10:57 .
drwxr-xr-x 21 root root 4096 2007-08-16 22:59 ..
-rw-r--r--  1 root root 2227 2005-10-13 04:04 .bashrc
-rw-------  1 root root   16 2007-08-17 11:48 .esd_auth
drwx------  3 root root 4096 2007-08-21 10:09 .gconf
drwx------  2 root root 4096 2007-08-21 10:15 .gconfd
drwx------  3 root root 4096 2007-08-20 10:58 .gnome2
drwx------  2 root root 4096 2007-08-16 22:55 .gnome2_private
-rw-r--r--  1 root root  141 2005-10-13 04:04 .profile
-rw-------  1 root root  255 2007-08-20 10:57 .recently-used
drwx------  3 root root 4096 2007-08-17 14:27 .synaptic

---

### Post by mikewhatever on 2007-08-21
> why don't I have a /root ? I had Vista installed and there is no ntfs? I'm trying to get grub to dual boot at startup. HELP!
Can you please rephrase that. Describe the situation coherently, specify what exactly are you trying to do and, if there are any errors, post them here.

---

### Post by forestpixie on 2007-08-21
run these in a terminal and post results

```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

---

### Post by dewcansam on 2007-08-21
well first you should know what hard drives you have in your system. i.e. 
120gb on primary master 
cdrom on primary slave
80gb on secondary master
nothing on secondary slave
(this is for ide / pata drives) in linux we refer to primary master as hda, primary slave as hdb, secondary master as hdc, secondary as hdd - now knowing that try this:

$sudo fdisk -l /dev/hda
$sudo fdisk -l /dev/hdb
$sudo fdisk -l /dev/hdc
$sudo fdisk -l /dev/hdd

and post your output

sudo = SuperUser DO - allows you to do commands as the root/sysadmin user (if you want use: $sudo -i = allows you to enter superuser interactive shell)
fdisk = partition manager for linux - allows you to view, edit partitions in linux using the shell
-l = lists all partitions for device
/dev/hda = primary master hard disk device

---

### Post by Bethrine on 2007-08-21
Okay, I am not exactly sure how to do what I want. I defragged my original install of Vista and then installed ubunto (see signature). On install it partitioned my hard drive for me at about 50%. I can find the partitions on my hard drive (discovering I also had a Vista back-up partition) and I found grub in my system because it loads in the terminal, but when I restart I automatically boot into Ubuntu. I want the option of booting into windows. Very new here, please be patient with me. P.S. I am not too computer literate.

---

### Post by Bethrine on 2007-08-21
sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1092     8771458+   7  HPFS/NTFS
/dev/sda2            1093        7699    53070727+   7  HPFS/NTFS
/dev/sda3   *        7700       14408    53890042+  83  Linux
/dev/sda4           14409       14593     1486012+   5  Extended
/dev/sda5           14409       14593     1485981   82  Linux swap / Solaris

and

cat /boot/grub/menu.lst             very long

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by sailor2001 on 2007-08-21
when you start to boot up. The screen shows all the partitions, etc. If you start to count down from ububtu (generic) as 0 (that is the default) to your windows home edition and remember that #...Now from the terminal, type in gksudo gedit boot/grub/menu.lst and in the 1st paragraph it will list as "default 0"  change that to the number you wanted to automatically boot into (windows, I guess)  Exit and save.

---

### Post by Bethrine on 2007-08-21
fdisk: invalid option -- /

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Bethrine on 2007-08-21
I want grub to ask me which to boot into at each startup. My main objective is to be able to use AutoCAD which I was told in another forum won't run with wine and read that the ntfs converters are still being tweaked.

---

### Post by forestpixie on 2007-08-21
> **sailor2001 said:**
> when you start to boot up. The screen shows all the partitions, etc. If you start to count down from ububtu (generic) as 0 (that is the default) to your windows home edition and remember that #...Now from the terminal, type in gksudo gedit boot/grub/menu.lst and in the 1st paragraph it will list as "default 0"  change that to the number you wanted to automatically boot into (windows, I guess)  Exit and save.
 
There isn't a windows grub option - that I think is the problem - it shows in fdisk -
/dev/sda2

I'm not sure about adding to grub - but I saw this in another thread as being added to get win into the grub menu - I'm assuming that hd0,2 boots the linux partition so hd0,1 would boot the win one ? 

Can someone check that out - in which case you would need to add this to your menu.lst.

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


title           Microsoft Windows
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```

But I'd be waiting for a second opinion here ;)

---

### Post by Bethrine on 2007-08-21
sorry, copied and pasted and I get no results for any of them. :(

---

### Post by forestpixie on 2007-08-21
what's the result of this now

cat /boot/grub/menu.lst

---

### Post by dewcansam on 2007-08-21
```
$sudo vi /boot/grub/menu.lst
```

then add these lines at this location: NOTE THE DIFFERENCES
```

....
title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
boot

title Windows Vista
root (hd0,0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

try that and see what happens
GL

---

### Post by Bethrine on 2007-08-21
thank you! I'll wait for that second opinion as this is my only computer. 

Found this earlier...

grub> root
 (fd0): Filesystem type unknown, partition type 0x0

---

### Post by Bethrine on 2007-08-21
grub> cat /boot/grub/menu.lst

Error 12: Invalid device requested

grub> sudo vi /boot/grub/menu.lst

Error 27: Unrecognized command

---

### Post by schorsch on 2007-08-21
It could also be /dev/sda1 that Vista is living on, so please change your file /boot/grub/menu.lst from
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


title           Microsoft Windows
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```
to 
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


title           Microsoft Windows
root            (hd0,***_0_***)
savedefault
makeactive
chainloader     +1
```
.. but I am not sure as I never run Vista before ...

... but an ~8 GB Vista Partition would be rather small ....

---

### Post by forestpixie on 2007-08-21
mixed posts now :)

I think that dewcansam has got it though, I just found another thread as I said not too sure - the first two partitions on your drive are ntfs :oops:

dewcansam - why are you getting the op to add the memtest again though?

Edit - there you go 2 think hd0,0, but yes 8Gb is a bit small?

---

### Post by schorsch on 2007-08-21
> **dewcansam said:**
> ```
$sudo vi /boot/grub/menu.lst
```

then add these lines at this location: NOTE THE DIFFERENCES
```

....
title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
boot

title Windows Vista
root (hd0,0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

try that and see what happens
GL

... it is better to put the windows boot information after the line "### END DEBIAN AUTOMAGIC KERNELS LIST" as otherwise an update could destroy this entry.

---

### Post by Bethrine on 2007-08-21
Yeah, 8gb is the backup I found with ubuntu that vista created once upon a time.

---

### Post by Bethrine on 2007-08-21
will this give me the option of where I want to boot at startup or automatically boot me somewhere?

---

### Post by forestpixie on 2007-08-21
in which case if Vista is still loaded and hasn't been borked it'll be on hd0,1

I'd wait 10 mins and let everyone who's been looking catch up :)

---

### Post by dewcansam on 2007-08-21
> **schorsch said:**
> ... it is better to put the windows boot information after the line "### END DEBIAN AUTOMAGIC KERNELS LIST" as otherwise an update could destroy this entry.

noted thx

---

### Post by Bethrine on 2007-08-21
lol, hah, I'm usually the one catching up  :)

p.s....

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
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
"/boot/grub/menu.lst" 142L, 4051C                             1,1           Top

I only got the end of the screen?

---

### Post by forestpixie on 2007-08-21
> **Bethrine said:**
> will this give me the option of where I want to boot at startup or automatically boot me somewhere?

at the moment you should have 3 seconds to make any choice
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3
```

this 3 can be changed to whatever you like 

at the moment can you access your ntfs partitions from within Ubuntu - just to look - in particular which partition has the Windows directories in - it'll either be sda1 or sda2 - knowing that will make editing the grub a bit easier I think.

---

### Post by dewcansam on 2007-08-21
> **forestpixie said:**
> mixed posts now :)
dewcansam - why are you getting the op to add the memtest again though?


wasn't trying to get you to add memtest again :) was showing WHERE to place the lines

but even i was wrong 

so add the lines```

title Windows Vista
root (hd0,0)
makeactive
chainloader +1
```

at the very end

---

### Post by schorsch on 2007-08-21
> **dewcansam said:**
> wasn't trying to get you to add memtest again :) was showing WHERE to place the lines

but even i was wrong 

so add the lines```

title Windows Vista
root (hd0,0)
makeactive
chainloader +1
```

at the very end
o.k. we found out that Vista will probably live on /dev/sda2 so the line starting with root has to look like ```
root (hd0,1)
```

---

### Post by Bethrine on 2007-08-21
/tmp/disks-conf-sda2  found it in disks manager

---

### Post by forestpixie on 2007-08-21
> **dewcansam said:**
> wasn't trying to get you to add memtest again :) was showing WHERE to place the lines

but even i was wrong 

so add the lines```

title Windows Vista
root (hd0,0)
makeactive
chainloader +1
```

at the very end

wasn't sure what was going on as I've only there once or twice myself :)

as far as the hd0,0 or hd0,1 - OP is sure that the first partition is the vista backup - would that boot? 

- I'm not good with vista only seen it once - came here from win2k - always stayed 1 ver behind MS - and did this instead of getting XP :D

---

### Post by forestpixie on 2007-08-21
> **schorsch said:**
> o.k. we found out that Vista will probably live on /dev/sda2 so the line starting with root has to look like ```
root (hd0,1)
```

That's what I would of thought too - if not it can be changed :)

---

### Post by Bethrine on 2007-08-21
ok, add this...

title Windows Vista
root (hd0,1)
makeactive
chainloader +1

to the end of this?...

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
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
"/boot/grub/menu.lst" 142L, 4051C                             1,1           Top

---

### Post by Bethrine on 2007-08-21
> **forestpixie said:**
> wasn't sure what was going on as I've only there once or twice myself :)

as far as the hd0,0 or hd0,1 - OP is sure that the first partition is the vista backup - would that boot? 

- I'm not good with vista only seen it once - came here from win2k - always stayed 1 ver behind MS - and did this instead of getting XP :D

Yes, Partitin 1 is backup (I think because is so small) and Partition 2 is much bigger ntfs and Partition 3 is just this  /

all according to ubuntu, I know I never would've found it in any windows.

---

### Post by forestpixie on 2007-08-21
yep - add it to the very end after the 'End of Debian automagic' bit

you can backup first if you like :)

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.bak.2108
```

```
gksudo /boot/grub/menu.lst
```

then reboot - if you want to give yourself more time to choose then change the 3 near the beginning of the file

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout [COLOR="Red"]3[/COLOR]
```

---

### Post by schorsch on 2007-08-21
Are you using "vi"? Then "SHIFT-G" will bring you to then end of the file. Despite of it, yes, add the following section to /boot/grub/menu.lst at the end:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```
If using "vi" press "ESC" then ":" and then "wq". If not .... save it anyway!

---

### Post by dewcansam on 2007-08-21
:lolflag: we got it going on now

simply put 
root (hd0,0) = /dev/sda1
root (hd0,1) = /dev/sda2

based on:
Device       Boot  Start   End    Blocks          Id System
/dev/sda1           1        1092   8771458+   7 HPFS/NTFS
/dev/sda2           1093  7699   53070727+ 7 HPFS/NTFS

i looked at sda1 and thought that would be primary windows partition
:confused:

---

### Post by schorsch on 2007-08-21
> **dewcansam said:**
> 
i looked at sda1 and thought that would be primary windows partition
:confused:
sda1 - sda4 are primary windows partitions ... when you start working with logical partitions that have to reside in an extended parttions the case is a little bit more complicated ...

---

### Post by Bethrine on 2007-08-21
please excuse my ignorance but...

> **forestpixie said:**
> yep - add it to the very end after the 'End of Debian automagic' bit

you can backup first if you like :)

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.bak.2108
```

```
gksudo /boot/grub/menu.lst
```

then reboot - if you want to give yourself more time to choose then change the 3 near the beginning of the file

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout [COLOR="Red"]3[/COLOR]
```[/QUOTE]

I don't see it :(  the debian bit that is

is the gksudo part for finding everything if it doesn't work unfortunately new to backing up too, I know, I know.

can I use 

less vi /boot/grub/menu.lst

to go page by page to enter the number part?  :blush:

*edit*  double blush  oh...

---

### Post by forestpixie on 2007-08-21
the debian bit is this at the very end

### END DEBIAN AUTOMAGIC KERNELS LIST

and yes you can use vi, schorcsh gave the commands in his last post - I just tend to use gedit but i forgot to put that in the code :oops: - getting tired now in my defence :)

```
gksudo gedit /boot/grub/menu.lst
```

sorry bout that, the backup worked though yes?

:)

---

### Post by Bethrine on 2007-08-21
Just because this is my ONLY computer, it should look like this?

kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
                                                              142,1         Bot
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

then I press Esc, type wq [enter] and save it anyway

---

### Post by Bethrine on 2007-08-21
just a sec, trying it now....:) .....

---

### Post by Bethrine on 2007-08-21
here's what I got...

$ sudo cp /boot/grub/menu.lst /boot/grub/menu.bak.2108
Password:
$ gksudo /boot/grub/menu.lst
sudo: /boot/grub/menu.lst: command not found
$


(do you think it's okay to hikjack your own thread??)

---

### Post by forestpixie on 2007-08-21
yes I believe so nearly :) - where did the line that says

142,1 Bot

come from - and the esc, type wq bit I've nveer done but I assume so

---

### Post by forestpixie on 2007-08-21
> **Bethrine said:**
> here's what I got...

$ sudo cp /boot/grub/menu.lst /boot/grub/menu.bak.2108
Password:
$ gksudo /boot/grub/menu.lst
sudo: /boot/grub/menu.lst: command not found
$


(do you think it's okay to hikjack your own thread??)

hijack away :D

you need to go read replies ;) - I already apologised for giving you bum steer:)

```
gksudo /boot/grub/menu.lst
``` should be ```
gksudo gedit  /boot/grub/menu.lst
```

---

### Post by schorsch on 2007-08-21
... the line starting with 142 has to be deleted or commented with a # at the start ... and the esq. wq commands are simply editor commands inside of vi: This is an editor that works on ANY *nix machine: Linux, SUN, HP, IBM, SGI .. whatever you want and it is always the same ... nice to know that :-)

---

### Post by Bethrine on 2007-08-21
Sorry bout that, I found it, no problem. 

cathy@Bethrine:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.bak.2108
cathy@Bethrine:~$ gksudo gedit /boot/grub/menu.lst

(gedit:10893): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I got it up in gnome too now, lol. Was using the terminal. The "bot" was in the bottom right of the terminal and the number was in the middle, both on the bottom. I have no idea what that warning is about? 

Sorry, I found your fix after I posted, oops. :)

---

### Post by forestpixie on 2007-08-21
cool - all done,saved and rebooted now I hope then

---

### Post by Bethrine on 2007-08-21
big blush, scared to do it. doing it now...eek...

---

### Post by Duck2006 on 2007-08-21
Edit your menu.lst for the windows entry so it looks like this, it may help

title Windows Vista
root (hd0,1)
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
makeactive
chainloader +1

---

### Post by Bethrine on 2007-08-21
dang it, I tried to edit it in the terminal, using the vi command to bring it up, and it won't let me. :cry:

can I do it in gedit?  Maybe that's what you meant all along?  ugh. feeling stupid here.

---

### Post by Duck2006 on 2007-08-21
Try

sudo gedit /boot/grub/menu.lst

---

### Post by forestpixie on 2007-08-21
do it in gedit then - same command as before - don't worry about the Gnome GUi warning

```
gksudo gedit /boot/grub/menu.lst
```

then save and reboot


just to reiterate this is what you should be adding

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```

as an aside use gksudo for graphical applications and sudo for others

---

### Post by Bethrine on 2007-08-21
ok, got it up in grub? i think...

edited and saved in the grub gui (thanks) to this...

root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by forestpixie on 2007-08-21
erm ... that's not it all is it?

I hope that's just the end of the file ;)

---

### Post by Bethrine on 2007-08-21
oh, looks like this now...

should I just edit the windows entry as Duck2006 suggested instead? confused again.

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
timeout		25

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by forestpixie on 2007-08-21
I don't know what his/her suggestions actually achieve to be honest - I see you changed your timeout :D heh heh 

I would go with what you've got unles Duck2006 comes back with some info - I've got to go now so good luck - I will look in in the morning to see that you've marked thread solved :)

If you do have a problem you can boot into recovery mode and replace the edited menu.list with the backup

if you need the command (which I'm sure you won't) its

```
sudo mv /boot/grub/menu.bak.2108 /boot/grub/menu.lst
```

---

### Post by Bethrine on 2007-08-21
oops didn't directly reply, just submitted a post. hope that doesn't make it hard for you to find.

nevermind...

---

### Post by Bethrine on 2007-08-21
k, gonna do it. thank you and everyone!!  

...writing down that command  :grin:

---

### Post by Bethrine on 2007-08-22
Morning all, well, for me anyway. 

I restarted this morning (I did it yesterday too, but my brain was just gone) and was able to get the options for booting by pressing Esc during the boot sequence, yay! Windows was there, but stalls over and over during it's startup so I am going to input duck2006's suggestion and see how that goes.

Aside: sorry if I was a bit short yesterday, I was trying very hard to keep up and wrap my mind around what was going on (i.e. yes forestpixie, I used your advice on the seconds delay at boot, very helpful!  :-D  among others) thank you all so much!

Here goes.....

Ok, it loads windows either way. The second way offered the option of either start or fix and start. (Maybe because I got impatient and physically shut it down and maybe because of the change Duck2006 suggested?) Start gave me a long slow process and fix and start was long and slow and I ended up with a blank screen so I physically shut it down again (have no idea what else to do). So grub is working and my problem now, I think, is that windows may be corrupted or something. So I will mark this thread as solved when someone can confirm I'm right that it's now my windows application and grub is working fine. ......Stupid windows. All those changes and in ubuntu and ubuntu's still working like a pro, Thank God!

forestpixie, you mentioned something about looking at windows through ubuntu? I'm very interested! :)

---

### Post by Bethrine on 2007-08-22
p.s.  the end of the file now looks like this....

root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista
root            (hd0,1)
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by jamvegan on 2007-08-22
If you don't want to have to press ESC to see the menu, then you can edit the section of menu.lst near the top:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

Comment out the last of those three lines by adding a # at the beginning, so it looks like:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

(BTW, if you highlight sections of code, such as when you post the contents of menu.lst, and then click the "#" at the top of the message window, you won't get the smilies in your post.)

---

### Post by Bethrine on 2007-08-22
Yes, that will help a lot. Thanks! Gonna do it tomorrow though. Ran out of time today.My eyes are glazing over.

---

