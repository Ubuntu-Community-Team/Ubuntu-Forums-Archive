---
title: "Cant boot into Ubuntu 1st time!!!!"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Talon-Skave on 2007-05-09
Hi guys 'n girls, I have a strange problem. It may have a simple solution(I hope). I am running a dual boot of Windowzzzzz xp and Ubuntu 7.04 (until I am comfortable using Linux and can remove XP).They are installed on seperate HDD's. 

I added a new (3rd) HDD to my current windows PC and installed Ubuntu on it. I can see all OS's in grub no problem and can boot into windows and ubuntu. However when I first turn on my PC(cold boot?) and select Ubuntu it  hangs before the GUI starts up. Kinda like it does if you mess up X. Although if I boot into Windows first(from a cold boot?) and then restart and select Ubuntu I can log into the desktop no problem. 

This wasnt an issue at first because I would always boot into Windows initially and then perhaps have a tinker in Ubuntu afterwards, but I'm finding my self logging into Ubuntu more and more at start up. Having to go into Win xp first and restart(as you can imagine) is begining to take its toll on my patience lol. I do not wish to remove Windows XP just yet.

Any help would be greatly rec'd

Thanks in advance

Talon Skave

---

### Post by beaudoin996 on 2007-05-09
what is in /boot/grub/menu.lst

---

### Post by Mutal1ty on 2007-05-09
I had the same issue
heres what to do, at boot when grub comes up, highlight the (generic) one and hit E for edit.
next screen that comes up will have several lines of code, highlight the one that has the Kernel name in it, and press e for edit
when you have a cursor at the end of the line after "quiet splash" type the following ```
vga=771
```
hit enter then b for boot

IF this works you should come to the graphical login. Go ahead and login.

at this point that change is not permanant, you will need to do the following to make it so:

Open a terminal

to back up your menu.lst fie:
```
sudo cp  /boot/grub/menu.lst  /boot/grub/menu.lst.bak
```
Then you edit the menu.lst file with this command:
```
sudo gedit /boot/grub/menu.lst
```
It will open it in a separate window; scroll through this until you find a section that looks like this:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hdXX ro
# kopt=root=/dev/hdXX ro 
```
On the Line that starts with "# kopt" add the command **vga=771** to the end of the line. It should look like this:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hdXX ro
# kopt=root=/dev/hdXX ro **vga=771 **
```
save the file, close the file.
then in the Terminal type this command:
```
sudo update-grub
```
This will update GRUB from the menu.lst file and viola your done.  Your next boot should go fine by hitting enter on generic.

---

### Post by Talon-Skave on 2007-05-09
Hi guys, thanks for the replies. Mutal1ty I tried what you suggested but I still cannot log into the desktop on my first boot up :( .  

Here is the /boot/grub/menu.lst file if it helps :


## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=91ff24b8-832a-4d5f-b8c9-ca974288381f ro


I noticed differences with the one you had. I tried putting the vga=771 at the end of all three #kopt lines and no joy :(. Any other ideas?

Thanks in advance

Talon Skave

---

### Post by Austin_KW on 2007-05-09
I dont think it will have much effect if you dont remove the comment '#' symbols

---

### Post by beaudoin996 on 2007-05-09
> **Talon-Skave said:**
> 
Here is the /boot/grub/menu.lst file if it helps :

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=91ff24b8-832a-4d5f-b8c9-ca974288381f ro


My menu.lst file has a lot more lines than this.  You just put a part of the header

---

### Post by Cappy on 2007-05-09
```

sudo gedit /boot/grub/menu.lst

```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
kopt=root=UUID=91ff24b8-832a-4d5f-b8c9-ca974288381f ro vga=771

---

### Post by Talon-Skave on 2007-05-10
Ahhh I see so I just need to remove the #. Im at work at the moment so will try it when I get home. Thanks again all. Will post back if I still have probs.

Talon-Skave

---

### Post by Talon-Skave on 2007-05-10
Hi guys, just got back from work and tried to edit the menu.lst. 
It still doesn't work :( here is the full menu.lst:
I did notice that when I sudo update-grub it undoes what I edited. So I tried once with updating grub and once without. Still no joy :(


# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
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
kopt=root=UUID=91ff24b8-832a-4d5f-b8c9-ca974288381f ro vga=771

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=91ff24b8-832a-4d5f-b8c9-ca974288381f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=91ff24b8-832a-4d5f-b8c9-ca974288381f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

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

---

### Post by nickpaton on 2007-05-10
Make sure you save your grub file before you close it.

---

### Post by Talon-Skave on 2007-05-10
Ahh that could be it. Gonna try that now. Thanks.

PS sorry about all the obvious things Im very new to Linux/Ubuntu

---

### Post by nickpaton on 2007-05-10
> **Talon-Skave said:**
> sorry about all the obvious things Im very new to Linux/Ubuntu

No worries mate - we're happy to help any time.

Good luck and welcome to the forums and ubuntu BTW!

---

### Post by Talon-Skave on 2007-05-10
> **nickpaton said:**
> Make sure you save your grub file before you close it.

arghhhhh I tried that but still no joy LOL. Perhaps its something to do with windows???

ok this is what I did:
1. boot to grub select ubuntu generic and pressed E
2. Added vga=771 to the end of "quiet splash" hit enter
3. Pressed b to boot
4. sudo cp  /boot/grub/menu.lst  /boot/grub/menu.lst.bak
5. sudo gedit /boot/grub/menu.lst
6. Then editited the #kopt part with vga=771 and saved it.
7. before closing I tried to update grub. However I could not type any commands in the terminal. So I opened a new tab with the terminal and updated grub. 
8. Finally I closed the terminal and the menu.lst and shutdown.

---

### Post by nickpaton on 2007-05-10
I've been comparing your grub to mine, and by and large they are identical.

Can you please just clarify again the number of HDD's and what each one does.

EDIT: "I am running a dual boot of Windowzzzzz xp and Ubuntu 7.04 (until I am comfortable using Linux and can remove XP).They are installed on seperate HDD's.

I added a new (3rd) HDD to my current windows PC and installed Ubuntu on it. I can see all OS's in grub no problem"

It's just that I cannot see the 3rd HDD anywhere in your grub with ubuntu - I can see Windows on dev/hda1 and ubuntu on hd2,0 but not the 3rd HDD you mention.

What happens when you disconnect this 3rd disc?

---

### Post by Talon-Skave on 2007-05-10
> **nickpaton said:**
> I've been comparing your grub to mine, and by and large they are identical.

Can you please just clarify again the number of HDD's and what each one does.

It's just that I cannot see the 3rd HDD anywhere in your grub with ubuntu - I can see Windows on dev/hda1 and ubuntu on hd2,0 but not the 3rd HDD you mention.

What happens when you disconnect this 3rd disc?

Ok my system originally had just two HDDs on the 1st IDE channel. 40gb for Windows and a 200gb for data storage.

I then purchased a thrid drive(80gb) and intalled it on the 2nd channel to install ubuntu on.
Now I have 2 NTFS HDDs from my original setup plus the extra drive for ubuntu.

I havent disconnected any drives as yet. 
Hope that makes sense

Talon-Skave

---

### Post by nickpaton on 2007-05-10
Right - got you now!

Can you try disconnecting the storage disc and see what happens and get back to us.

---

### Post by Talon-Skave on 2007-05-10
ok will do thanks again for all your help. Will try that tommorrow and post back.

Talon-skave

---

