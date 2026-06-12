---
title: "[SOLVED] Any fix"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-01-14
for the "you passed an undefined mode" problem at bootup?  its just annoying....

---

### Post by nikoPSK on 2008-01-14
Could I have a photo or more information please? :confused:

Best,
nikoPSK

---

### Post by PeterJS on 2008-01-14
I think it has to do with the vga= options passed to the kernel at boot. I know for nvidia cards that can be safely removed, you won't have the cool high res frame buffers for physical terminals, but for as much use as they get would it be such a loss. Don't know about other cards, ATI cards might be black magic and require it.

---

### Post by nikoPSK on 2008-01-14
> **PeterJS said:**
> I think it has to do with the vga= options passed to the kernel at boot. I know for nvidia cards that can be safely removed, you won't have the cool high res frame buffers for physical terminals, but for as much use as they get would it be such a loss. Don't know about other cards, ATI cards might be black magic and require it.

ah, now I know what hes talking about...:lolflag: Thanks peter.. I'm still a n00b at heart.

---

### Post by sports fan Matt on 2008-01-14
Peter's right...Im just not sure what type of card i have..

---

### Post by nikoPSK on 2008-01-14
> **sox fan Matt said:**
> Peter's right...Im just not sure what type of card i have..

You can open your case up or check under system info. :KS

---

### Post by sports fan Matt on 2008-01-14
think i found it...does this look right?  Intel Corporation 82810 CGC (Chipset Graphics Controler?)  Does that sound right or remotely close?

---

### Post by PeterJS on 2008-01-14
That's certainly possible, I don't have the entire intel product line memorized. The quickest way in software to figure out what graphics card you have is:
```

lspci | grep VGA

```

---

### Post by sports fan Matt on 2008-01-14
that command ran gave me: VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)

---

### Post by nikoPSK on 2008-01-14
> **sox fan Matt said:**
> that command ran gave me: VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)

so that's your card :D

nikoPSK

---

### Post by sports fan Matt on 2008-01-14
would reconfiguring the xserver org work or is that out of the question for my problem?

---

### Post by ajmorris on 2008-01-14
> **sox fan Matt said:**
> for the "you passed an undefined mode" problem at bootup?  its just annoying....

Hi there, could you please post you /boot/grub/boot.conf file.
On the kernel line of your entry for your current kernel, there will be a vga=SOMETHING line, just remove that from the kernel line, and that annoying message will disappear.

---

### Post by ajmorris on 2008-01-14
> **sox fan Matt said:**
> would reconfiguring the xserver org work or is that out of the question for my problem?

that is not needed, after removing the vga=something line from what i suggested in my post, you can always just change vga=something to a correct vga mode, although, vga= is not required unless you wanna change the resolution of your boot screen

---

### Post by nikoPSK on 2008-01-14
> **sox fan Matt said:**
> would reconfiguring the xserver org work or is that out of the question for my problem?

you can try:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

---

### Post by nikoPSK on 2008-01-14
> **ajmorris said:**
> that is not needed, after removing the vga=something line from what i suggested in my post, you can always just change vga=something to a correct vga mode, although, vga= is not required unless you wanna change the resolution of your boot screen

oh, well fine then... :p

---

### Post by ajmorris on 2008-01-14
> **nikoPSK said:**
> you can try:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```nikoPSK

No, and xorg reconfigure is not needed for a simple vga kernel line on boot.

---

### Post by sports fan Matt on 2008-01-14
if i remove it from when The machine boots up and I can remove the vga =795 from the lernel, why does it not "remove it" that same message pops up when i restart the machine for some reason...

---

### Post by ajmorris on 2008-01-14
> **sox fan Matt said:**
> if i remove it from when The machine boots up and I can remove the vga =795 from the lernel, why does it not "remove it" that same message pops up when i restart the machine for some reason...

How strange, if a wrong vga= code is not being passed through... then you should not get that error message, unless your video chip doesnt support the default vga mode.
Could you please paste your /boot/grub/menu.lst file?

---

### Post by sports fan Matt on 2008-01-14
Can you please inform me how?  (I feel like such a NooB)

---

### Post by nikoPSK on 2008-01-14
> **sox fan Matt said:**
> Can you please inform me how?  (I feel like such a NooB)

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by sports fan Matt on 2008-01-14
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=97a8801a-d5ce-42a7-86c8-ab2c8558e4a9 ro

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
# defoptions=quiet vga=795

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=97a8801a-d5ce-42a7-86c8-ab2c8558e4a9 ro quiet vga=795
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=97a8801a-d5ce-42a7-86c8-ab2c8558e4a9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by ajmorris on 2008-01-14
where it says:

```
 kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=97a8801a-d5ce-42a7-86c8-ab2c8558e4a9 ro quiet vga=795
```

towards the bottom of the file...
remove the vga=795 (as root) save the file, then reboot, and the annoying message will be gone :D

---

### Post by nikoPSK on 2008-01-14
> **ajmorris said:**
> where it says:

```
 kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=97a8801a-d5ce-42a7-86c8-ab2c8558e4a9 ro quiet vga=795
```towards the bottom of the file...
remove the vga=795 (as root) save the file, then reboot, and the annoying message will be gone :D

then please mark this thread as "SOLVED"
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Best,
nikoPSK

---

### Post by thelatinist on 2008-01-14
> **nikoPSK said:**
> ```
sudo gedit /boot/grub/menu.lst
```

For future reference it might be better to recommend

```
sudo cat /boot/grub/menu.lst
```

No point in opening the file for editing if he doesn't have to, especially since you didn't suggest he back it up.  There's always the off chance he could ctrl + x instead of ctrl + c...

---

### Post by nikoPSK on 2008-01-14
> **thelatinist said:**
> For future reference it might be better to recommend

```
sudo cat /boot/grub/menu.lst
```No point in opening the file for editing if he doesn't have to, especially since you didn't suggest he back it up.  There's always the off chance he could ctrl + x instead of ctrl + c...

Ah, thanks. Learn something every day. :)

nikoPSK

---

### Post by thelatinist on 2008-01-14
> **ajmorris said:**
> where it says:

```
 kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=97a8801a-d5ce-42a7-86c8-ab2c8558e4a9 ro quiet vga=795
```

towards the bottom of the file...
remove the vga=795 (as root) save the file, then reboot, and the annoying message will be gone :D

Before you even open this file for editing you should do:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

---

