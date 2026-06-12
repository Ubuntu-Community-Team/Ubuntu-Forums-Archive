---
title: "[SOLVED] grub stage1 question"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Walc on 2008-03-23
Hello all
im having error 17 : cant mount selected partition issue here. Now i dont remember what where my linux partitions so ive went to partitions manager in live cd. This is what i got < i have 1 sata drive>:
dev/sda1 ---- its my vista nfts partition (~25gb)
dev/sda2 ---- everything whats left, which is:
                      >sda5 ---- its my 2nd vista partition
                      >sda6 ---- my 3rd vista partition
                      >sda7 ---- ext3 
                      >sda8 ---- ext3
                      >sda9 ---- swap
                      >sda10 --- my 4th vista partition

/find /boot/grub/stage1  returns me with >>>> hd0,6 

Now few words of explanaition, i actually remember creating 3 linux partitions, it workde like a charm, but then came up this error 17 thing and since then i cant run ubuntu anymore <7.10>...id like to fix this since i had it pretty much set up.

My questions are:
- hd0,6 is related to which one of the above partitions? shouldnt it be sda7-9 ??
- what has happened to sda 3-4
- why im having sda instead of hda?
- what r u advising me now in order to recover my linux ?

[http://i29.tinypic.com/v7gi29.png](http://i29.tinypic.com/v7gi29.png)

[http://i27.tinypic.com/xdcc5k.png](http://i27.tinypic.com/xdcc5k.png)

---

### Post by ikonia on 2008-03-23
I would guess the the problem is your partition map has changed without your device.map being updated.


mount your ubuntu partition and look at what grub is mapping your disks to in /boot/grub/device.map.

hda has become sda due to the update to libata in glibc

---

### Post by Walc on 2008-03-23
will do that once im back 2morrow
thx for ur response m8
btw. howcome my partition map has changed?...

---

### Post by Walc on 2008-03-24
> **ikonia said:**
> I would guess the the problem is your partition map has changed without your device.map being updated.


mount your ubuntu partition and look at what grub is mapping your disks to in /boot/grub/device.map.

hda has become sda due to the update to libata in glibc

mate _**device.map**_ content in my case is...:

(hd0)   /dev/sda

i must say i expected a  bit more here....what shall i do next in order to restore my beloved ubuntu?

also heres my **_menu.lst_** content:

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
# kopt=root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,8) 

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic 
root		(hd0,8) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
quiet 

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root		(hd0,8) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 

title		Ubuntu 7.10, memtest86+ 
root		(hd0,8) 
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

### Post by ikonia on 2008-03-24
your device.map looks fine,

thats good.

What's worth looking at is your grub setup and your menu.lst that you've posted.

what you need to do is work out what your root option is.

your find suggests that your root option should be (hd0,6)

try that, 

I don't think it's that, I think it's either (hd0,3 or 4) depending on which ext partition contains /boot.

---

### Post by Walc on 2008-03-24
> **ikonia said:**
> 

your find suggests that your root option should be (hd0,6)

try that, 

I don't think it's that, I think it's either (hd0,3 or 4) depending on which ext partition contains /boot.

how can i find out what my root option is?

---

### Post by ikonia on 2008-03-24
the hd options refer to /dev/sdaX

as you have only 2 ext3 partitions it must be one of those.

Try both options to find out which is it as I don't know which has your /boot partition on .

---

### Post by Walc on 2008-03-26
funny thing is..../boot is on the 24gb partition...>>>>>>>>  which is sda1...<my vista partition>
im confused here....lolz

---

### Post by ikonia on 2008-03-26
/boot is not on your vista partition, it will be on either a.) your / partition, or b.) it's own stand alone /boot partition.

---

### Post by Herman on 2008-03-27
:) Hello Walc,
Try this, 
```
## ## End Default Options ## 

title		Ubuntu 7.10, kernel 2.6.22-14-generic 
root		(hd0,6) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
quiet 

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root		(hd0,6) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 

title		Ubuntu 7.10, memtest86+ 
root		(hd0,6) 
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
```
Change the 8's to 6's and see if that works.

Here's a link about how to do that, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD.[COLOR=#666666][/COLOR]

Regards, Herman  :)

---

### Post by Herman on 2008-03-27
Okay, sorry about the brevity.
> - hd0,6 is related to which one of the above partitions? shouldnt it be sda7-9 ??To explain a few things, Grub starts counting at zero instead of one, so hard disk number 1 is (hd0), and hard disk 2 is (hd1) to GRUB, third hard disk is (hd2), and so on.

It's the same thing with partitions, start counting from zero.
First hard disk, partition 1 is (hd0,0).
First hard disk, partition 2 is (hd0,1)
and so on.

So, first hard disk, partition 7 will be (hd0,6), which is your Ubuntu install, exactly where GRUB told you it is when you did 'find /boot/grub/stage1'. That's what I think your /boot/grub/menu.lst needs to be corrected to.

Ignore the boot flag, that's only important to Windows. I am guessing that's what you mean when you say '/boot is on the Windows partition'. That confused me for a while, in Linux lingo, what you said means something else entirely. We don't care about the boot flag. To us a /boot partition means the partition where the boot loader files and the Linux kernel are housed. It can be a separate partition from the rest of our files.

> - what has happened to sda 3-4The partition numbers 1,2,3 and 4 are reserved only to be used by up to four primary partitions or three primary partitions and one extended partition.
Inside an extended partition, if you decide to make one, which is usually a good idea, the logical partitions begin counting at 5.
So you must have had just one primary partition to begin with, then you made an extended, that's number 2, and the logical partitions begin with number 5, and count up from there.
That is as it should be.
> - why im having sda instead of hda?ikonia has answered that.
> - what r u advising me now in order to recover my linux ?Boot your Ubuntu Live CD.
```
sudo mkdir /media/ubuntu
```
```
sudo mount -t ext3 /dev/sda7 /media/ubuntu
```
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```
Change the 8's to 6's like the example in the post above.
That should fix it.

Regards, Herman :)

---

### Post by Walc on 2008-03-27
thx for ur response Herman
im at wrk atm
will try ur ways in few hrs once im back

ok i assume that this code u have posted in #10 is a part of menu.lst right? shall i overwrite it?

i still dont get what did u mean by saying change 8's to 6's - was it UUID numbers in fstab ?

---

### Post by Herman on 2008-03-27
:) Yes, I think you need to change this
```
# menu.lst - See: grub(:cool:, info grub, update-grub(:cool: 
#            grub-install(:cool:, grub-floppy(:cool:, 
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
default        0 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout        10 

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
# title        Windows 95/98/NT/2000 
# root        (hd0,0) 
# makeactive 
# chainloader    +1 
# 
# title        Linux 
# root        (hd0,1) 
# kernel    /vmlinuz root=/dev/hda2 ro 
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
# kopt=root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,8)

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic 
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-generic 
quiet 

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root        (hd0,8) 
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro single 
initrd        /boot/initrd.img-2.6.22-14-generic 

title        Ubuntu 7.10, memtest86+ 
root        (hd0,8)
kernel        /boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title        Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title        Windows Vista/Longhorn (loader) 
root        (hd0,0) 
savedefault 
makeactive 
chainloader    +1
```to this:
```
# menu.lst - See: grub(:cool:, info grub, update-grub(:cool: 
#            grub-install(:cool:, grub-floppy(:cool:, 
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
default        0 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout        10 

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
# title        Windows 95/98/NT/2000 
# root        (hd0,0) 
# makeactive 
# chainloader    +1 
# 
# title        Linux 
# root        (hd0,1) 
# kernel    /vmlinuz root=/dev/hda2 ro 
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
# kopt=root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,6) 

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic 
root        (hd0,6) 
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-generic 
quiet 

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root        (hd0,6) 
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=6fd0df6d-614b-4cf9-abe6-576e57a0ac41 ro single 
initrd        /boot/initrd.img-2.6.22-14-generic 

title        Ubuntu 7.10, memtest86+ 
root        (hd0,6) 
kernel        /boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title        Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title        Windows Vista/Longhorn (loader) 
root        (hd0,0) 
savedefault 
makeactive 
chainloader    +1
```Regards, Herman :)

---

### Post by Walc on 2008-03-27
Herman !!!
you are a life-saver
its working fine now
once again thanx

---

