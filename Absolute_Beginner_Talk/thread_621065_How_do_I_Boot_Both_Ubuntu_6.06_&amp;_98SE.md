---
title: "How do I Boot Both Ubuntu 6.06 &amp; 98SE"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by StGeorge on 2007-11-23
My 98SE is on a 10GB Hard Drive.
My Ubuntu 6.06 is on the beginning of a 120 GB Hard Drive.
It takes the first 10GB the rest is Fat32 Storage.
I wish to either Boot both OS's or if that is not possible I wish to get the 98SE set as the default OS at Boot.
Please do not refer me to any articles.
I have spent months on and off trying to make sense of them.
It seems that any advice given in these articles is designed for experienced users.
The reason for me wanting to do the above is that I cannot and will not spend more time trying to configure Ubuntu to allow other computers on my Network namely XP and 98SE Laptops to access the Internet via Linux version of Internet Connection Sharing.
Presently my Desktop Computer is configured with 98SE Internet Connection Sharing.
As I can only use Ubuntu when nobody else requires the internet it is seldom used at all.
I keep it in the vain hope that one day Ubuntu will have a Graphical interface for both Networking and Booting.
If nobody can help with the above then possibly someone could advise me on how to rid myself of Grub and use a graphical Boot Loader instead.
I have Partition Magic with PQ Boot manager but it does not recognise the Ubuntu OS.
Any help would be appreciated.

---

### Post by natehatewindows on 2007-11-23
you need to install GRUB in ubuntu. i would suggest downloading a super grub disk (goolge it) and it should maybe take you throught the process in ubuntu already has grub installed. you will want to "restore grub". i am also sure you wil get a lot of replys here so just be a little patient. i will tell you more if you dont but i am in a little hurry right now..sorry

---

### Post by natehatewindows on 2007-11-23
please post  the output of 

```
fdisk -l 
``` 

do this in a terminal in ubuntu.

sounds liek to just need to add a grub entry for windows. please tell me where windows is i.e. /dev/hda1 for example.

---

### Post by natehatewindows on 2007-11-23
download and burn to cd two things...

super grub disk

and gparted boot disk

these will be handy for you, maybe not now but soon i think. gparted is way better that partition magic and will work with all different formats.

---

### Post by natehatewindows on 2007-11-23
please give more detail also about your network setup....thanks,

---

### Post by banewman on 2007-11-23
You are a little ambiguous with your system status.
If you are trying to dualboot - have two OS's on the one comp you cannot have both running at the same time. Is that what you want?
With windows installed if you then install ubuntu you will get - at boot time - a menu to select the OS you want to boot. This is called the grub menu.
Can you explain more carefully what you are trying to do?

---

### Post by spiderbatdad on 2007-11-23
editting the /boot/grub/menu.list file is not too hard.
find the file by```
gksudo gedit /boot/grub/menu.list
```
then look for Default 0.
it should look like this:# menu.lst - See: grub(8), info grub, update-grub(8)
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
**default		0**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

**Now scroll down the list till you see a section that looks like this:**

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0f88ce89-3a7e-44a7-8a17-5659224d7294 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0f88ce89-3a7e-44a7-8a17-5659224d7294 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=0f88ce89-3a7e-44a7-8a17-5659224d7294 ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=0f88ce89-3a7e-44a7-8a17-5659224d7294 ro single
initrd		/boot/initrd.img-2.6.22-12-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

[B]Count how many options are there including and before windows. For example, if windows is 4th on the list and the first one is considered zero then windows is 5.
change the Default value (mentioned earlier) to 3 and save your settings. Reboot and windows should load by default. Sorry you're having a hard time. Even windows took time to learn at first blush.[/B]

---

### Post by StGeorge on 2007-11-23
Thanks to all of you for the response.
At the moment I am given the option to boot either system but Ubuntu is set as default.
Because I use Bios for my password I sometimes forget to wait until I get the boot option and it automatically boots into Ubuntu.
I then have to restsart to boot into 98SE.
Yes I was nieve enough to think it may be possible to switch between the two OS's at the click of a mouse.
I will read what is posted and get back.

---

### Post by banewman on 2007-11-23
If you follow the above post about editing /boot/grub/menu.lst you can set win98 as the default by changing the line - defautl 0

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0    <<<< this one

to the one that corresponds to your win98 - remember to count each block of text starting from 0. :)

---

### Post by StGeorge on 2007-11-23
Tried Spiderbatdad in terminal and got error.
I have opened up the file from the menu 1st folder.
It is read only.

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
# kopt=root=/dev/hdb2 ro

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

title		Ubuntu, kernel 2.6.15-29-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

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

### Post by StGeorge on 2007-11-23
I already have what natehatewindows is suggesting but I worry that if I start messing with GParted etc I will mess up my present injstallations.
I also have lilo and various other boot loaders untried as I do not want mess anything up.

---

### Post by spiderbatdad on 2007-11-23
sorry the default value would be 3 if windows was 4th on the list...the first option being 0

---

### Post by spiderbatdad on 2007-11-23
you can also leave the Default value at 0 and move the block of text describing your windows os to the top of the list of boot options...

---

### Post by StGeorge on 2007-11-23
thanks natehatewindows for thinking bout the network side but triust me I will not go down that road again.
I tried it for months.
Given up all hope.
It is basically simple.
My 98SE Desktop has a newkink 5 way ethernet adapter.
It allows XP and 98SE to commect via the Desktop with Winblows ICS.
I have no problems with this.
I would love to use Ubuntu as my main OS on this Desktop but as I said above I have tried and will not try again.
I will wait until someone is smart enough to create a graphical interface as I never was into command line anyway.

---

### Post by StGeorge on 2007-11-23
thanks spiderbatdad  but I still cannot edit the dammed file.
I cannot get into the thing.

---

### Post by spiderbatdad on 2007-11-23
open a terminal and type:
```
sudo gedit /boot/grub/menu.list
```

this will open a GUI text editor for you. just save after you edit.

by the way, i think you want to  leave out the line that says "save default" in that block of text if you move it to the top of  the list of boot options. I'm not an expert but I did this on my mother's comp. and it worked perfectly there after. Give it a try. where else could you have this much fun?

---

### Post by StGeorge on 2007-11-23
I got a blamk page with nothing to edit

---

### Post by StGeorge on 2007-11-23
I think I might have more fun on a Phychiactric Ward

---

### Post by spiderbatdad on 2007-11-23
use the path to file name that you used to open the file when you posted an output earlier.

```
sudo gedit /boot/grub/what.ever
```

or open your text editor graphically: Applications->Accessories->Text Editor

when it open chose File->Open
then browse your file system to find it...not your home directory

---

### Post by banewman on 2007-11-23
A blank page means your creating a new page. That should be  - 
sudo gedit /boot/grub/menu.lst          (that is a small L) :)

---

### Post by StGeorge on 2007-11-23
still just a blank page.
I did this in terminal.
sudo gedit /boot/grub/menu.1st

All I get is a blank page.
Nothing to edit.
I reckon that's it for me.
I can see another 4 months on and off trying to simply chamge a default for boot.
Utter madness.

---

### Post by spiderbatdad on 2007-11-23
it's menu.lst 
as in list.
sorry man there is a bit of a learning curve, but it's worth it.

---

### Post by banewman on 2007-11-23
St George - did you type a one then st at the end?
Should be a small L then st  - 
sudo gedit /boot/grub/menu.lst :)

---

### Post by StGeorge on 2007-11-23
Thanks for all your help everyone.
I think it will be another 6 months before I try anything like this again.
I hope this will help someone else though.
Giving up and going back to good old 98SE.
ps I happen to intensly dislike XP.
Next stage maybe a MAC.
Will keep Ubuntu as a secomd OS just to play music on.
I love AMORAK.
Will get into the MBR and delete Grub.
Will try other Boot Loaders.

---

### Post by StGeorge on 2007-11-23
Yes banewman I did.
What a fool I am

---

### Post by banewman on 2007-11-23
Your in a club with many members mate  :)

---

### Post by spiderbatdad on 2007-11-23
aye!

---

### Post by StGeorge on 2007-11-23
The problem is I still cannot see what I am supposed to edit.
Is it chainloader next to windows

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-29-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

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

### Post by spiderbatdad on 2007-11-23
that whole block of text:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows 95/98/Me
root (hd0,0)
savedefault
makeactive
chainloader +1

should be moved to the top of the list of boot options:

## ## End Default Options ##

title Ubuntu, kernel 2.6.15-29-386
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-29-386 root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.15-29-386
savedefault
boot

title Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-29-386 root=/dev/hdb2 ro single
initrd /boot/initrd.img-2.6.15-29-386
boot

title Ubuntu, kernel 2.6.15-28-386
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.15-28-386
savedefault


put it below ##END DEFUALT OPTIONS##


but i believe you should leave out the line that says "save default"

---

### Post by banewman on 2007-11-23
Use right click and cut & paste. :)

---

### Post by StGeorge on 2007-11-23
Have done will try reboot now thanks again

---

### Post by banewman on 2007-11-23
Best of luck :)

---

### Post by StGeorge on 2007-11-23
You guys out there are great.
I Chickened out on the cut and paste and copied and pasted instead.
I now have the 98SE set as default and have it at the bottom of the boot options too.
When I have more time I will try to sort the Network out so that I can use Ubuntu as mty main OS.
I have two other laptops which I tried to install 7.10 on with no success.
However I am happy with 6.06 at the moment.
Thanks again all:guitar:

---

### Post by banewman on 2007-11-23
Glad we all could help you out. :)
Laptops are a bit more work but mostly it is not too hard. :)

---

### Post by StGeorge on 2007-11-23
I am now back into Ubuntu after rebooting from 98SE.
Below is how my menu.lst (abbrev for list) and not 1st (first) as I tried initially in Terminal.
I now have it in both Places.
Default and other OS's.

I hope this will help others.
Easy Peasy Lemon Squeezy. ( I wish).:)
Thanks again.

## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.15-29-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

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

### Post by natehatewindows on 2007-11-24
im not sure what you did but you only need one of the windows entry. I think you added the top one  making windows default so you should just delete the bottom one....it wont hurt anything to have it there but it sucks you have the same entry two time....not goo looking ;) glad yo got help....how for that network. maybe buy a switch and use that instead of WIN 98??? if i understood right you have 5 computers running into this bot to get internet? i would just buy a router or a switch and you would not have any problems and i bet you would have better speeds too. do you have cabel, dsl? what connection? you could even just go wifi but then you would need to buy hardware for all your computers.....but its great for laptops....i like sitting on the couch surfing the web :)

---

