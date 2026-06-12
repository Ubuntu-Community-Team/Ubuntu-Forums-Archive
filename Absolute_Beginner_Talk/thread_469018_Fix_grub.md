---
title: "Fix grub?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-06-09
Hi I've installed windows xp after installing Ubuntu. And grub disappeared.
How can I fix it? The only thing I have is a ubuntu desktop cd.

---

### Post by xthund3rh3adx on 2007-06-09
GRUB disappered because windows installs its own MBR (Master Boot Record).

To reinstall GRUB, use a GRUB installation disk, or use the Ubuntu Alternate Install CD to skip to the installation step of installing grub to the "/" mount point.

---

### Post by the_axiom on 2007-06-09
[QUOTE=xthund3rh3adx] or use the Ubuntu Alternate Install CD to skip to the installation step of installing grub to the "/" mount point.[/QUOTE]

Sorry for my bad understanding, but I didn't get that. How can I fix grub using the live cd?

---

### Post by alienexplorers on 2007-06-09
Insert and boot live cd
Enter terminal
enter > sudo grub
enter > find /boot/grub/stage1
you will get an output like (hd#,#)
enter > root (hd#,#)
enter > setup (hd#)
exit the grub program editor.
reboot and you should get a complete grub menu.

---

### Post by the_axiom on 2007-06-09
Thanks for the replay I'll try that immedetly. But is there any way to make the grub menu appear on keypress? Meaning it would be unvisible untill I press a certain key at bootup?

---

### Post by alienexplorers on 2007-06-09
Not that I am aware of.

---

### Post by the_axiom on 2007-06-09
I tried to do as you told me. But it all got so wrong.
The grub menu now appears. 
But first of all I have 3 OS installed; Vista, XP and Ubuntu.
In the grub menu only ubuntu and vista appears.
And when I choose Vista it boots up XP instead. And that XP dosen't look good, it appears in very bad resolution and 16 colors...

How can I undo the installation of grub?

---

### Post by the_axiom on 2007-06-09
I now this is a forum and the responses may delay, But I'm in a hurry. I need very quick help please.

---

### Post by ubername on 2007-06-09
> **the_axiom said:**
> I now this is a forum and the responses may delay, But I'm in a hurry. I need very quick help please.


What do you need all the OS's for? I'm also a newbie and when it goes wrong I tend to reinstall OS's. I know I have to install Vista first, but once that is done the whole process takes about an hour. BACKUP YOUR DATA FIRST I accidentally moved my 'Documents and Settings' folder on my XP drive through Ubuntu magic, and it was, ahem, difficukt to get back.

---

### Post by the_axiom on 2007-06-09
> **ubername said:**
> What do you need all the OS's for? I'm also a newbie and when it goes wrong I tend to reinstall OS's. I know I have to install Vista first, but once that is done the whole process takes about an hour. BACKUP YOUR DATA FIRST I accidentally moved my 'Documents and Settings' folder on my XP drive through Ubuntu magic, and it was, ahem, difficukt to get back.

Because the computer is not only used by me.

I fixed the low resolution. But Why isn't Vista appearing on that list? It says Vista but it isn't, it's XP.

Useful information:
Ubuntu and Vista is on the same hard drive, different partitons. And XP on another hard drive partition.

---

### Post by logos34 on 2007-06-09
> How can I undo the installation of grub?

You could try to restore windows ntldr to the MBR by booting from the XP install cd, typing 'r' and doing the 'fixmbr' procedure.  It looks like the installation order was 1. vista, 2. ubuntu, and winxp last.  If so, the the xp bootloader would (should) include vista (i think--no experience with vista yet)--seems like when you boot XP from grub you should first get a DOS screen with a choice of vista or xp (from boot.ini file).  

If that gets you back into windows, then you could use the ubuntu live cd to fix your menu.lst and whatever else, and install grub to a floppy for the time being so you can get into linux as well.

Need some more sys info.  Might help to run 
sudo fdisk -l 
from the live cd just to give us an idea of what your paritions look like, and maybe post your menu.lst if you want.

---

### Post by logos34 on 2007-06-09
> **the_axiom said:**
> Because the computer is not only used by me.

I fixed the low resolution. But Why isn't Vista appearing on that list? It says Vista but it isn't, it's XP.

Useful information:
Ubuntu and Vista is on the same hard drive, different partitons. And XP on another hard drive partition.

Posted right before me.

So you can boot into ubuntu also?

You might want to post that menu.lst so we can see about the xp/vista mixup.

---

### Post by the_axiom on 2007-06-09
> **logos34 said:**
> Posted right before me.

So you can boot into ubuntu also?

You might want to post that menu.lst so we can see about the xp/vista mixup.

Here you go:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		6

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
# kopt=root=UUID=fd64451b-761f-48d7-98ea-5a7fc90ecdcf ro

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
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fd64451b-761f-48d7-98ea-5a7fc90ecdcf ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fd64451b-761f-48d7-98ea-5a7fc90ecdcf ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fd64451b-761f-48d7-98ea-5a7fc90ecdcf ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fd64451b-761f-48d7-98ea-5a7fc90ecdcf ro single
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
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by logos34 on 2007-06-09
My hunch (because I do not have any experience with vista) is that grub is chainloading the windows bootloader as modified by XP (it was the last to be installed), and XP is listed on some boot.ini file (either on it's own drive or on vista C:\) with both OS's listed but with XP as default, ahead of vista, AND the timeout is set to 0, which is why the DOS screen does not appear.  Just a guess.

---

### Post by the_axiom on 2007-06-09
> **logos34 said:**
> My hunch (because I do not have any experience with vista) is that grub is chainloading the windows bootloader as modified by XP (it was the last to be installed), and XP is listed on some boot.ini file (either on it's own drive or on vista C:\) with both OS's listed but with XP as default, ahead of vista, AND the timeout is set to 0, which is why the DOS screen does not appear.  Just a guess.

How can I fix this? Should I install Ubuntu over again, to "refresh" the grub?
This was my installation order of the operative system installations: Vista --> Ubutnu --> XP

---

### Post by logos34 on 2007-06-09
> How can I fix this? Should I install Ubuntu over again, to "refresh" the grub?
This was my installation order of the operative system installations: Vista --> Ubutnu --> XP

Yes, but check this first.
(edit: yes as in reinstall just grub).

In nautilus file browser go to your windows root directory (aka C:\) on both disks and look for boot.ini (if you do it in windows you'll have to specify in the location bar 'C:\boot.ini' (it's a really hidden file).  

One of them might have both OS's listed with XP as default and like a 0 or 1 second timeout. (I had to change mine to 10 while I was setting up a linux install from windows disk/netboot).

---

### Post by the_axiom on 2007-06-09
Ok.
I found this on my vista pratition:
> [boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

But on the partition with windows XP I couldn't find any boot.ini.

---

### Post by logos34 on 2007-06-09
Sorry for the delay.

Try adding changing your boot.ini file thus:

> [boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

**multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Vista" /noexecute=optin /fastdetect /usepmtimer**
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

This will hopefully bring up the dos screen and allow you to boot into vista.  

But if you want your windows partitions to show up in grub menu and boot DIRECTLY to the correct disk, you could try this:

Take out the entry for XP in the above file.  Then create a new boot.ini file on the XP disk in C:\ like this:

> [boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS

[operating systems]
 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

Then you would add an entry for XP to the bottom of grub like this:

> title		Windows XP Professional
root		(hd1,**1**)      *corrected
map		(hd0) (hd1)
map		(hd1) (hd0)
savedefault
makeactive
chainloader	+1

And then restore grub again as you did before (although you might not have to do that). 

Not sure if it'll work with vista, though.

---

### Post by the_axiom on 2007-06-09
When I try to edit the file, it says the disk is write-protected...
Edit: nvm fixed it

---

### Post by the_axiom on 2007-06-09
I tried to do the first one.
But It didn't work. The grub menu was as usual, but when I pressed on the windows Vista boot up.
I got the possibility to choose of 2 alternetives which had the same name. Only one of them worked (windows XP) and the other one just gave me a black screen.

Excuse me for my bad understanding but I didn't really get what your second tip does?

EDIT: for some strange reason the ntfs partitions disappeared from the Ubuntu default file browser after restart.

---

### Post by logos34 on 2007-06-09
> When I try to edit the file, it says the disk is write-protected...

oh, I sorry forgot about that...I've been using ntfs-3g for so long to write to windows that I hardly even think of it anymore.

> Excuse me for my bad understanding but I didn't really get what your second tip does?

Basically I was trying to make it so that you could boot directly to xp on its own disk instead of having one extra step of the bootloader on the vista/ubuntu drive.  You need a boot.ini file on the drive (you said it's blank or not there) because grub chainloads it -- basically hands off the boot process to windows. But as it turns out you can't even get the first step to work properly.  

This is getting a bit complicated, but there's got to be a relatively simple way to get it sorted...lemme look this over a bit

...anyone else please feel free to jump in here...

---

### Post by logos34 on 2007-06-09
In the meantime, give [SuperGrub]("http://supergrub.forjamari.linex.org/") a try.  I was just hoping there was an easier way to fix the windows files by hand.

---

### Post by logos34 on 2007-06-09
You may have better luck the other way round by including an XP entry in Vista's boot files using [VistaBootPro]("http://www.vistabootpro.org/") and take out the boot.ini file deposited by XP in vista C:\ directory.  Then when you select Vista in grub menu you might actually get it to boot for a change, with a choice to go to XP on the other drive.

Add: 
It seems that the install order is criticall -- should be XP-->Vista-->linux.  Check out this link 
[TriBooting-with-Unbuntu]("http://www.techspot.com/vb/all/windows/t-69612-TriBooting-with-Unbuntu.html")

---

### Post by the_axiom on 2007-06-10
**** all this crap, I'll just format everything. And begin all over.

Thank you for your help.
 Honestly I'm a Microsoft-user because of the hardware- and game-support. But there's one thing that I can't take away from you -** the support**. It's sick how good the support is. I get fascinated every single time.

---

