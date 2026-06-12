---
title: "Error on grub 17"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by trachycarpus on 2006-12-18
I hope I have done the correct thing in startin a new thread but the replies to my original one have become lost amongst other queries in my thread. 
To precis my query:-I downloaded Mandriva onto Hdb6, Ubunto on Hdb7, WinXP on Hda1. 
On reboot I get error17 when choosing Ubunto in the grub menu. Windows boots OK. I have reinstalled grub as per instructions but nothin else has helped. I was advised to reformat Hdb but it has a partition on it with windows bits which I do not want to lose. I have downloaded the iso of Gparted but this fails to load, only going round in circles after the message:-
Disabling irq14, hd9 lost interrupt, irq14 nobody cared disabling irq14, ide0 on irq14. There is a lot of other writing but to much to write. 
Any suggestions would be very gratefully rec'd.

---

### Post by John E on 2006-12-18
**trachcarpus** - according to your other thread, hdb7 is a FAT32 volume. Do you mean that you installed Ubuntu on hd1,7? In that case it would equate to hdb8.

Boot up from the live CD. Open up a terminal window and type **sudo grub**. Then enter your maintenance password. After that, type **root (hd1,7)** and let me know what output you see.

---

### Post by trachycarpus on 2006-12-18
I told you I was getting confused, Typed sudo grub Command not found.
Sorry if I do not reply instantly, I'm at work again and won't be back till lunch. No peace for the wicked.

---

### Post by John E on 2006-12-18
Well, my guess then is that Ubuntu is actually installed on hdb8, not hdb7. Your best bet might be to just install it again onto the same partition.

---

### Post by trachycarpus on 2006-12-18
Success, thanks to the leads here, I did an edit at grub loading time and changed the root settings and i'm in. Now I just need to know how to edit the grub permanently and I'll be there. Also how do I add the Mandriva to the grub?
Thanks all
Peter

---

### Post by John E on 2006-12-18
> **trachycarpus said:**
> Now I just need to know how to edit the grub permanently and I'll be there.
The only way I know of is by using **sudo grub** but that doesn't seem to work on your system. The only thing I can suggest is that you open a terminal window, change to the **/sbin** directory and try again - or alternatively, try **sudo /sbin/grub**

> **trachycarpus said:**
> Also how do I add the Mandriva to the grub?
Inside the folder **/boot/grub** you'll see a file calle **menu.lst** (that's a lower case 'L' by the way, not a number '1'). Make a safety copy of it, then open it in a text editor. At the bottom, you'll see how the other volumes are mounted so just find the one for Ubuntu, copy it as Mandriva and change the necessary parameters.

---

### Post by trachycarpus on 2006-12-18
Now I'm into Ubunto properly sudo grub does /did work so your assistance would be appreciated.
Peter

---

### Post by John E on 2006-12-18
Peter - the quickest thing might be if you post the text from **/boot/grub/menu.lst**. I'll then add the necessary lines and post it back again.

---

### Post by trachycarpus on 2006-12-18
only gives "no such file or directory"unfortunately.:confused: 
Its not easy this linux is it?

---

### Post by bulldog on 2006-12-18
Try```
gksudo gedit /boot/grub/menu.lst
```
Or ```
cat /boot/grub/menu.lst
```

---

### Post by John E on 2006-12-18
> **trachycarpus said:**
> Its not easy this linux is it?

Ain't that the truth..!! Try this....

Go to **Places->Search for files**. Change L**ook in folder** so that it reads **File System**. In the box that says **Name contains** type **menu.lst**. It should find a file by that name in a folder called **/boot/grub**. Left-click on that file and open it. Then paste the contents here.

---

### Post by trachycarpus on 2006-12-18
Went in another way and got the following in gedit
 menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=be0e1811-7f91-49ce-905a-f3c11ec3d24d ro
# kopt_2_6=root=/dev/hdb7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

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
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb7 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,6)
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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2
title		Microsoft Windows XP Home Edition
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

I temperarily changed the details to roothdb7 from 6 and /dev/hdb7 to hdb8 and booted from there and am in Ubunto now.

---

### Post by John E on 2006-12-18
Before long, you're going to need to log in as **root**. Do you know how to do that?

---

### Post by trachycarpus on 2006-12-18
Assuming this means using my password, yes.

---

### Post by John E on 2006-12-18
At the login screen, log in as  **root** and add these lines at the bottom of **menu.lst**. But _before you change anything_ you need to find the relevant text to replace the bits where I've written INSERT#1 and INSERT#2.

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb6.
title		Mandriva (on /dev/hdb6)
root		(hd1,5)
kernel		/boot/I**NSERT#1** ro root=/dev/hdb6 rhgb quiet 
initrd		/boot/I**NSERT#2**
savedefault
boot
```

To find the relevant text, mount your Mandriva partiton - then enter the /**boot** folder. Inside it, you'll see a file beginning with the name **vmlinuz**. Copy its _name_ to the clipboard and paste it instead of the text INSERT#1

In the same folder, you'll see a file whose name begins with **initrd**. Copy its _name_ to the clipboard, then paste it instead of the text INSERT#2

Now save the **menu.lst** file (to do this, you'll need to be logged in as **root**). Next time you re-boot, you should see an entry in the Grub menu that will take you into Mandriva.

---

### Post by trachycarpus on 2006-12-18
Thanks for the help.
"To find the relevant text, mount your Mandriva partiton - then enter the /**boot** folder. Inside it, you'll see a file beginning with the name **vmlinuz**. Copy its _name_ to the clipboard and paste it instead of the text INSERT#1"

Don't forget I'm a newbie, I assume to mount means sudo mount hdb6, if not how is this accomplished. thebit about the insert etc makes sense but finding it is the problem.
Peter

---

### Post by John E on 2006-12-18
Try typing this at a terminal prompt.

**sudo mkdir /media/hdb6 && sudo mount -a**

It's possible that you might need to re-boot after doing that. I can't quite remember.

---

### Post by dannyboy79 on 2006-12-18
> **John E said:**
> Try typing this at a terminal prompt.

**sudo mkdir /media/hdb6 && sudo mount -a**

It's possible that you might need to re-boot after doing that. I can't quite remember.

simply doing mount -a will mount everything within fstab and won't know that it needs to mount his particular hdd partition to the /media/hdb6 folder. 

you need to create a folder like he states, "sudo mkdir /media/whateveryouwant".
then you'll need to mount the hdd and partition that your boot stuff is on. if it is in fact hdb6, then simply do "sudo mount /dev/hdb6 /media/whateveryouwant" then you would do "cd /media/whateveryouwant" then just look for the boot folder and look for the files he was referring to. post back if you need more help. Later

---

### Post by trachycarpus on 2006-12-18
Set up directory for mandriva, mounted, went through desktop, double clicked and it says I do not have permission to view files. given up for a moment.
Will progress with the grub mods first.
Thanks all
peter

---

### Post by trachycarpus on 2006-12-18
Had menu.lst in gedit , changed all the relevant partition numbers, went to save, Cannot save as you do not have the relevant permissions. As I'm working from root what other permissions do I need and where do I get them. Regretting trying to install mandriva now, Ubunto was working well before this.
Peter

---

### Post by trachycarpus on 2006-12-19
Well I've solved the boot error 17 thanks to all that helped. It seemed that sudo gedit would not work for me, however gksudo gedit did. It just asked for my password, found menu.lst, edit with correct partition numbers, save and voila.
Job for tonight is Mandriva.
Cheers
Peter

---

