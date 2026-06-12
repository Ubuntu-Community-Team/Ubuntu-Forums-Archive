---
title: "partition manager help"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by ksujason on 2008-01-05
I continue to have a problem after installing ubuntu. After rebooting the syatem always tries to boot only to the cd.
I was told from an earlier post to put my results from the partition editor on here for evaluation. I can open the editor, but i am not sure how to put the results on here.

Thanks for the help

---

### Post by forestpixie on 2008-01-05
click post reply - then one of the little icons looks like a paperclip - it will open the attach form - you can browse to the scrnshot and upload

---

### Post by ksujason on 2008-01-05
I opened up the partition manager and took a screen shot. Hopefully this works.

---

### Post by forestpixie on 2008-01-05
that looks alright - can you open terminal and post the output from this please

```
cat /boot/grub/menu.lst
```

---

### Post by thelatinist on 2008-01-05
Did you by any chance disable boot from HD in your bios in order to get your computer to boot from the Live CD?

---

### Post by forestpixie on 2008-01-05
op has done that he says in his other thread - > After starting the reboot and removing the cd I went into bios and changed the boot order back to the hard disk.

---

### Post by ksujason on 2008-01-05
> **forestpixie said:**
> that looks alright - can you open terminal and post the output from this please

```
cat /boot/grub/menu.lst
```

when I type that in, it comes back with "no such file or directory"

---

### Post by forestpixie on 2008-01-05
try pasting or if you typed it in the 1 is in fact a lower case L

---

### Post by ksujason on 2008-01-05
ok, I tried it with a lower case l again. It comes back with "no such file or directory".

Does it sound like I need to try reinstalling?

Thanks

---

### Post by forestpixie on 2008-01-05
you might need to install grub, paste this in a terminal and give us the output

```
ls /boot/grub/*
```

---

### Post by ksujason on 2008-01-05
It says "no such file or directory" when I try that command.

---

### Post by forestpixie on 2008-01-05
oh whoops - just realised you won't if you're in the livecd - which I think you are

Open nautilus - places > computer

once it's open - I think you should see all the partitions marked as 'volumes of someGb size'

try to open the partition which corresponds to the ubunut installation, if it doesn't allow you to - try to open it from the terminal with
```
gksudo nautilus
```

once you've got the partition open - navigate to the /boot/grub directory - you can then open menu.lst directly from there

copy and paste the file into a post here

be very careful not to do anything to the file - you'll have it open as root

---

### Post by ksujason on 2008-01-05
Ok, here it is. Sorry it is very long.

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
# kopt=root=UUID=db7f56c0-9b12-4327-90fe-bf8a4443d4d3 ro 
 
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
 
title		Ubuntu 7.10, kernel 2.6.22-14-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=db7f56c0-9b12-4327-90fe-bf8a4443d4d3 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
quiet 
 
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=db7f56c0-9b12-4327-90fe-bf8a4443d4d3 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 
 
title		Ubuntu 7.10, memtest86+ 
root		(hd0,0) 
kernel		/boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by forestpixie on 2008-01-05
and you tried the suggestions from your other thread?

did you try supergrub - that looks to be right to me, assuming that you only have the one hard disc

---

### Post by ksujason on 2008-01-05
> **forestpixie said:**
> and you tried the suggestions from your other thread?

did you try supergrub - that looks to be right to me, assuming that you only have the one hard disc

I did try the suggestions from the other post. The only thing I did not try was supergrub. I do have only one hard drive, so I will do some searching to see if I can find out how to run it.

Thank you very much for all of your help.

---

### Post by ksujason on 2008-01-05
I downloaded supergrub, booted to it, and went through all of the steps. It finished succesfully. After rebooting it does the same thing asking me to insert a disk into the cdrom.
Does anyone have anything else they think I should try?

---

### Post by eternicode on 2008-01-05
What exactly is asking you to insert a cd?  Is it GRUB, or the BIOS, or what?

---

### Post by thelatinist on 2008-01-06
In your other thread you said that you are getting an error when you try to boot from the hard drive.  What is the exact wording of this error message?

---

