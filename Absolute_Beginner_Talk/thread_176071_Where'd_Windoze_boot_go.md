---
title: "Where'd Windoze boot go?"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by legolas on 2006-05-14
I have read an uncountable amount of threads about the grub boot loader and setting up dual boots, but I can't find anything that addresses putting Windows boot back after accidentally erasing it when installing Ubuntu.  
I did it right the first time, but I had to reinstall Ubuntu from scratch the second time because I could not, for the life of me, get the my backup to boot.  Unfortunately, I accidentally botched my Windows boot.  Now when I turn on my computer I see my various Ubuntus' , but windows is gone.  It is still hiding on the disk because I managed to make a boot disk to get into Windows.  
How do I put it back on the grub list???
Thanks guys

---

### Post by adam.tropics on 2006-05-14
Grub should have recognised it. The file to look at is /boot/grub/menu.lst Do a quick search here on restoring grub, there's loads up already.

---

### Post by adam.tropics on 2006-05-14
Have a read [here...]("http://www.ubuntuforums.org/showthread.php?t=168134&highlight=restore+grub")

---

### Post by legolas on 2006-05-14
No, my grub is fine-Ubuntu boots up great, it is just that Windows doesn't appear on the menu anymore so I can't get into Windows.  The /boot/grub/menu.lst is fine, just no Windows.

---

### Post by RRS on 2006-05-14
You should be able to put windows back into grub with:
 ```
sudo gedit /boot/grub/menu.lst

```

Here's an example of mine:
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-22-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-22-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-22-386
boot

title		Ubuntu, kernel 2.6.15-21-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-21-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-21-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-21-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
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

```

Hope this helps.

---

### Post by catlett on 2006-05-14
Don't worry this is easy as long as windows is still there. If I am understanding correctly you have windows and ubuntu installed. You want to have a menu option for both. This option will put a spot for windows on your grub menu. I am also going to assume windows is on the first partition of your first hard drive.
First you have to open the grub menu list ```
sudo gedit /boot/grub/menu.lst
```
Now hit enter a couple of time to put some places between the other entry and this. Put this into the menu
```
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
 Hit save in the window control. When you reboot windows will be an option. As long as it exists and is in the first partition of the first hard drive it will boot.

---

### Post by adam.tropics on 2006-05-14
> As long as it exists and is in the first partition of the first hard drive it will boot.

If it isn't,

> 
first partition on first hard drive = (hd0,0)            
first partition on second hard drive= (hd1,0)
2nd partition on first hard drive = (hd0,1)            
2nd partition on second hard drive= (hd1,1)
3rd partition on first hard drive = (hd0,2)             
3rd partition on second hard drive= (hd1,2)
 

---

### Post by legolas on 2006-05-14
You guys kick all kinds of butt, Thanks!

---

