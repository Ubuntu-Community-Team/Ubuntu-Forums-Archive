---
title: "Dual boot problems..."
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Niloc on 2007-09-20
I had a perfect system, one 80 gig drive with Windows 2000, one 40 gig drive with Ubuntu and a menu on boot to choose between them.
My wife wanted a Karaoke program and I bought a new AMD 64 computer for my Ubuntu. My wife took the old desktop down to the local guru to get a Karaoke program, when it came back all it had was Windows XP!! The Ubuntu drive was still there but the boot selection at startup had vanished, all it would do was run Win XP. no sigh of Ubuntu....

So I thought the best thing to do was what I did at first, install Ubuntu and my boot menu would re-appear.... Wrong, all I can get now is Ubuntu, Windows XP has vanished, no boot menu, nothing, just Ubuntu!!

My wife is not happy, I am not happy what have I done? I am sure both systems are there, they are on two separate hard drives but where us the boot choice menu?

The option of 'press del on startup' refuses to work, F4 offers a choice of one HD (Ubuntu), the floppy and the CD, F11 about the same.
Where is the boot menu supposed to be? What is its name? Can I edit it and what do I put in it?

Any assistance will be greatly appreciated....

Colin

---

### Post by Maestro23 on 2007-09-20
In terminal type the following and copy/past output here:

> cat /boot/grub/menu.lst (lower case L)

This will get the ball rolling.  The forum is good for help.

---

### Post by alienexplorers on 2007-09-20
Try reloading grub using the info in my sig.

---

### Post by Niloc on 2007-09-20
I reloaded grub, edited /boot/grub/menu.lst but I still cannot see WinXP! All I can get is Ubuntu!

---

### Post by alienexplorers on 2007-09-20
Please post your menu.lst file here.

---

### Post by Skidpad on 2007-09-20
Two things come to mind when I read this:

1: Are you sure XP is still there after you loaded Ubuntu?  Check or post the output of sudo fdisk -l for verification.

2: Post your grub file so we can see it, too.

(beat me to it alien...)

---

### Post by Maestro23 on 2007-09-20
> **alienexplorers said:**
> Please post your menu.lst file here.

Hey, didn't I ask for that. j/k :smile:

---

### Post by alienexplorers on 2007-09-20
Did not even notice.  Call me blind.
> **Maestro23 said:**
> Hey, didn't I ask for that. j/k :smile:

---

### Post by Niloc on 2007-09-20
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
timeout		3

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
# kopt=root=UUID=54189090-e24d-4e42-b4cc-33dda2d952fc ro
# kopt_2_6=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Niloc on 2007-09-20
sudo fdisk -l
puangsoi@puangsoi-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9963    80027766    7  HPFS/NTFS
puangsoi@puangsoi-desktop:~$

---

### Post by alienexplorers on 2007-09-20
Add this line to the bottom of your menu.lst file.

title Windows 95/98/NT/2000
root (hd1,0)  
makeactive
chainloader +1

---

### Post by Skidpad on 2007-09-20
And, presuming this is still your wife's computer, she may want it to boot XP without her manually selecting it from the grub screen during the boot sequence?  If so, you'll have to change your default option # up there at the top of the file.  (Remember you start counting OS/boot options from zero when choosing your default OS).

---

### Post by Niloc on 2007-09-20
alien, I did all that, now I still don't get the menu except by pressing Esc but if I select Windows all I get is a black screen  and 'Starting up...' but nothing else, no Ubuntu and no Windows....

---

### Post by alienexplorers on 2007-09-20
Try changing the last section of your menu.lst to:
> title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

---

### Post by meierfra on 2007-09-20
Since windows is on the second hard drive you need to use "map":

title Windows 95/98/NT/2000
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

---

### Post by alienexplorers on 2007-09-21
Meierfra,  Thanks for that info.  I never heard of doing that in ubuntu.

---

### Post by Niloc on 2007-09-21
Now I get 'Error 11: unrecognised device string', which string is the device string?

---

### Post by meierfra on 2007-09-21
You need a  "space"  between (hd0) and (hd1) ( and also between (hd1) and (hd0))

---

### Post by Niloc on 2007-09-21
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title           Microsoft Windows XP Professional
root            root(hd1,0)
                   map (hd1)(hd0)
                   map (hd0)(hd1)
                   savedefault
                   makeactive
                   chainloader +1  


### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by meierfra on 2007-09-21
As I thought, you missed the spaces. Also you have "root root (hd1 ,0)" it should be "root (hd1,0)"

It's easiest to just use copy and paste.

---

### Post by Niloc on 2007-09-21
spaces inserted, results exactly the same, ' unrecognised device string'

---

### Post by meierfra on 2007-09-21
Did you fix the "root root"?

---

### Post by alienexplorers on 2007-09-21
Did you reload grub?

Error 11=11 : "File not found"> 

This error is returned if the specified filename cannot be found, but everything else (like the disk/partition info) is OK.

---

### Post by Niloc on 2007-09-21
I usually do 'copy & paste' but the problem machine is across the other side of the room so it is bits of paper I am afraid.
I have remover the spare 'root', maybe it will work now?

---

### Post by meierfra on 2007-09-21
It should, but one never knows for sure.

---

### Post by Niloc on 2007-09-21
Now the last entry looks like this...

title         Microsoft Windows XP Professional
root         root(hd1,0)
                map (hd1)  (hd0)
                map (hd0)  (hd1)
                savedefault
                makeactive
                chainloader +1  


But when I call the menu with Esc, all I get are the Ubuntu entries, no Windows at all!

---

### Post by alienexplorers on 2007-09-21
title Microsoft Windows XP Professional
[COLOR="Red"]root[/COLOR]root(hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
savedefault
makeactive
chainloader +1 

Remove the root in red.
It should look like this:


Title Microsoft Windows XP Professional
root(hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
savedefault
makeactive
chainloader +1

---

### Post by meierfra on 2007-09-21
That is very strange. Can you post the whole  menu.lst with copy and paste?

Also  your still wrote "root root (hd1 ,0)"    make sure its is "root (hd1,0)"  Note that there should no  space between hd1 and the comma.

---

### Post by Niloc on 2007-09-21
I actually got the internet working on the problem machine, copied and pasted the correct solution but it still does not offer me Windows, just Ubuntu

---

### Post by meierfra on 2007-09-21
please post the whole "menu.lst" so that we can look for typos.

---

### Post by Niloc on 2007-09-21
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
timeout		3

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
# kopt=root=UUID=54189090-e24d-4e42-b4cc-33dda2d952fc ro
# kopt_2_6=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot


Title 		Microsoft Windows XP Professional
      		root(hd1,0)
      		map (hd1) (hd0)
      		map (hd0) (hd1)
      		savedefault
      		makeactive
      		chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by alienexplorers on 2007-09-21
title Microsoft Windows XP Professional
[COLOR="Red"]root (hd1,0)[/COLOR]    There should be a space between root and (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
savedefault
makeactive
chainloader +1

---

### Post by meierfra on 2007-09-21
and:

title must be in lower case ( that is what makes "windows" disappear from the grub menu)

---

### Post by alienexplorers on 2007-09-21
Thanks for the catch. I did not even realize I capitalized it.

---

### Post by Niloc on 2007-09-21
Some progress.... the lowercase fixed the menu problem, now I get 'NTLDR Missing, press Ctrl Alt Del to restart'

Why do I have to press Esc to make the menu appear, it always came up automatically...

---

### Post by meierfra on 2007-09-21
"NTLDR" I think is a windows boot file, but I'm not sure and don't know how  to  fix that.


The "esc" problem is easy: in the menu.lst look for the line

hiddenmenu

and change it to

#hiddenmenu

you might also want to change

timeout 3

to 

timeout 10

so that you have more time to change from "ubuntu" to "windows"

---

### Post by alienexplorers on 2007-09-21
Boot your windows disk into recovery mode and run fixmbr.  Reboot your computer.  Then follow the directions in my signature line for reloading grub from the live cd.

---

### Post by Niloc on 2007-09-21
I have made those changes,  I guess I had better start asking Bill questions to find out where 'NTLDR' is supposed to be.

Thank you for your patience and help, I thought I had another boat anchor to throw away...

Colin

---

### Post by alienexplorers on 2007-09-21
Sorry I could not have been more help!!!

---

