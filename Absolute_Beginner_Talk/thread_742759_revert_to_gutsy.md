---
title: "revert to gutsy"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by darkerlink on 2008-04-02
So I log into my computer tonight and see "514 important updates available" or something like that. Ok, I click on it and start downloading. Mind you, I am still very new to Ubuntu. So things started to update and unstall and I was required to reboot. "No problem", I thought. When Grub loaded, it now read "hardy" instead of "gutsy". I had no idea I was updating the whole OS. So I log in and tried to open Devede. It was gone. Ummmm. So I search for the software and tried to install it. I can't. I tried to play music. I can't. So I was very frustrated and search the forums if it was possible. So far I found I have to re-install. Is this true? If so, I'd like to suggest making it clear that Hardy was being installed. I had already known that it was in beta but I didn't know it was going to be install onto my computer. I thought this was a routine update. There was a lack of prompts and this experience has made me very cautious about trusting Ubuntu updates in the future.

Is there a way to revert back to 7.10?

---

### Post by spiderbatdad on 2008-04-02
could you post ```
cat /etc/lsb-release
```

also the contents of ```
cat /boot/grub/menu.lst
``` "L" as in list, not 1st.

---

### Post by darkerlink on 2008-04-02
first code I got:
```

set@set-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu hardy (development branch)"
set@set-desktop:~$ 

```

Second code, I got:

```

set@set-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), kernel 2.6.22-14-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu hardy (development branch), kernel 2.6.22-14-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

set@set-desktop:~$ 


```

---

### Post by spiderbatdad on 2008-04-02
ok. If you scroll down in /boot/grub/menu.lst

you will see:
```
## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), kernel 2.6.22-14-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu hardy (development branch), kernel 2.6.22-14-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4c1831c9-7124-4384-a41d-a3dad8afb8d4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


``` that section. And near the top a section that looks like this :

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0


```

The kernel that boots by default is this first one listed in the section of your kernels...it starts counting at 0, 1, 2, 3, and so on.
Apparently the 2.6.24-12 kernel is not detecting your hardware properly yet. You can use the earlier kernel by changing that default number to coincide with a 2.6.22-14 kernel...now I notice you have 2.6.22-14rt and 2.6.22-14 generic. I'm not sure which you want...I haven't seen "rt" before. At any rate you don't want to select a recovery mode. so try changing default to 2 and if that doesn't work, then change it to 4.

to edit the file you have to open it as a super user:
```
gksu gedit /boot/grub/menu.lst
``` save the file by clicking the little floppy disk image near the top of the window. Reboot.

Also you can set your update manager to check for and prompt you regarding "important security updates." Just navigate System>>Administration>>Software Sources>>Updates and select only security updates.

---

### Post by darkerlink on 2008-04-02
I have changed it to both 2 and 4. Now I am running 2 because I remembered loading the RT when gutsy was installed. Devede is still missing from the applications list and I still can't install it. So I open Synaptic Package Manager and search for Devede and mark it for installation when I get this prompt:

```

devede:
 Depends: dvdauthor  but it is not installable
 Depends: mencoder but it is not going to be installed
 Depends: mplayer

```

Also I have noticed that I am now using firefox 3 beta 4. I have checked only security updates to prevent this in the future. Is there a way to get Devede to work again. That program is very important to me. It is literally, my bread and butter right now.

---

### Post by spiderbatdad on 2008-04-02
have you tried ```
sudo apt-get install dvdauthor mencoder mplayer devede
```

---

### Post by darkerlink on 2008-04-02
got
```

set@set-desktop:~$ sudo apt-get install dvdauthor mencoder mplayer devede
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dvdauthor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dvdauthor has no installation candidate
set@set-desktop:~$ 

```

I'm almost ready to re-install 7.1 from the live CD. So frustrating. Thanks, ur my only help!

---

### Post by hyper_ch on 2008-04-02
> **darkerlink said:**
> So I log into my computer tonight and see "514 important updates available" or something like that. Ok, I click on it and start downloading. Mind you, I am still very new to Ubuntu. So things started to update and unstall and I was required to reboot. "No problem", I thought. When Grub loaded, it now read "hardy" instead of "gutsy". I had no idea I was updating the whole OS. [...] If so, I'd like to suggest making it clear that Hardy was being installed. I had already known that it was in beta but I didn't know it was going to be install onto my computer. I thought this was a routine update. There was a lack of prompts and this experience has made me very cautious about trusting Ubuntu updates in the future?

Sorry to say this, but updates won't just upgrade to a new OS version itself... once a stable release is out there you will even be prompted visually that you could upgrade to a new OS version...

So you actually invoked an upgrade to hardy somehow first place and this did not just happen as "normal update".

---

### Post by darkerlink on 2008-04-02
> **hyper_ch said:**
> Sorry to say this, but updates won't just upgrade to a new OS version itself... once a stable release is out there you will even be prompted visually that you could upgrade to a new OS version...

So you actually invoked an upgrade to hardy somehow first place and this did not just happen as "normal update".

I don't know if you are calling me a liar or saying I manually upgraded. All I know is that I logged into my account and was prompted to upgrade and I did so. I was not informed that I will be updating to hardy, whether it was stable or not. I don't really know what to tell you. If you could tell me how to revert back to gutsy or just get Devede to work agian, that would be much appreciated.

---

### Post by hyper_ch on 2008-04-02
I don't say you're a liar... all I'm saying is that it does not happen just like that and that you have must something to invoke a system upgrade... you might not recall it but you must have done that.

Reverting can only be done by reinstallation or putting an image back.... and Devede works fine for me in Hardy.

---

### Post by spiderbatdad on 2008-04-02
You should see dvd author in synaptic. If not check your software sources to make sure they are enabled.

---

### Post by caravel on 2008-04-02
> **darkerlink said:**
> I don't know if you are calling me a liar or saying I manually upgraded. All I know is that I logged into my account and was prompted to upgrade and I did so. I was not informed that I will be updating to hardy, whether it was stable or not. I don't really know what to tell you. If you could tell me how to revert back to gutsy or just get Devede to work agian, that would be much appreciated.

**hyper_ch** is correct, you have somehow performed a distribution upgrade.  I am still running 7.10 and it has never *once* prompted me to upgrade to 8.04 so I'm not sure how this has happened.  Did you follow any advice in the forums recently involving copying and pasting commands such as "apt-get dist-upgrade"?

---

### Post by darkerlink on 2008-04-02
Sweet! I got Devede installed! I went into Synaptic, then opened, repositories> and checked "Software restricted by copyright or legal issues (Multiverse)" Searched Devede and installed with no problem!

I am not sure I ran that code string. I just installed Ubuntu about 4 days ago and everything is quite new(and different) to me. There may be a possibility that I ran that code without knowing what it did. The most likely time was when I was trying to get Moblock installed but I ditched it for IPBlock but that was 2 days ago. The rest of the time, I installed from applications and/or synaptic. 

Although I didn't get Gutsy back, I am happy to get Devede back. Thanks guys for all the help! It's a rocky learning curve and now I know to come here for questions :)

---

