---
title: "boot loader menu"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by anorexicpillow on 2006-12-03
Hello... I was wondering if there was a place where i can download a boot menu.. I remember back a few years when i installed mandrake it installed a nice boot loader thing :)

---

### Post by Peepsalot on 2006-12-03
You mean like this?

[http://www.ubuntuforums.org/showthread.php?t=208855](http://www.ubuntuforums.org/showthread.php?t=208855)

---

### Post by anorexicpillow on 2006-12-03
i think so! I will try that out after mythbusters:P

---

### Post by anorexicpillow on 2006-12-03
ahhh this doesnt seem to be working... i dont know why but when i type in the commands to install the files it doesnt seem to find them it says no such file that was fine! help anyone?

---

### Post by Peepsalot on 2006-12-03
Can you copy and paste the exact commands and the results that you get?

---

### Post by anorexicpillow on 2006-12-03
wow i really seem to be running into problems with this now when i rebooted my windows partition wasnt on the boot menu here is what it says 

root@anorexicpillow:/home/anorexicpillow# sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
dpkg: error processing grub-gfxboot_0.97-5_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 grub-gfxboot_0.97-5_i386.deb

---

### Post by ciscosurfer on 2006-12-03
The file could be on your Desktop, in that case, you need to cd to your Desktop directory and run the command again.

---

### Post by Peepsalot on 2006-12-03
> **anorexicpillow said:**
> wow i really seem to be running into problems with this now when i rebooted my windows partition wasnt on the boot menu here is what it says 

root@anorexicpillow:/home/anorexicpillow# sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
dpkg: error processing grub-gfxboot_0.97-5_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 grub-gfxboot_0.97-5_i386.deb
Where did you download the file to?  You have to be in directory that contains the file.  If the file is on your desktop, then do this before running that command:
```

cd ~/Desktop

```

---

### Post by anorexicpillow on 2006-12-03
okay that seemed to work all up untill gfxmenu /boot/grub/message.suse # when i did that it said bash: gfxmenu: command not found

---

### Post by anorexicpillow on 2006-12-03
you know what... screw it.. instead i want my grub back to the way it was... the only problem is, is that while trying everything i could to get it to work i screwed up my menu.lst all seems fine except windows isnt on the list when i reboot, can you take a look at the menu to see what i can add so it sees my windows partition



gfxmenu /boot/grub/message.suse
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
# defoptions=

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

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Debian GNU/Linux, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Debian GNU/Linux, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Debian GNU/Linux, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by seshomaru samma on 2006-12-03
please post the output for 
```
sudo fdisk -l
``` (lower case letter L not number 1...)

---

