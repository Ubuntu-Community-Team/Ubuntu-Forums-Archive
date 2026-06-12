---
title: "issues with reaching xp partition"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by turtlewars on 2006-11-05
I'm a new Ubuntu user and just installed 6.06 yesterday, intending to create a dual-boot system.  My current partition setup, according to GParted, is that I have one partition that contains Ubuntu and another entirely separate partition that contains two other partitions within it, one with my Windows XP data in it and one designated as a linux swap point.  I can't, at current, get to XP from startup, as it's not one of my options listed in Grub, and GParted won't let me change any aspects of my current partition setup.  How can I either edit my current setup or somehow obtain access to Windows XP?

---

### Post by Ecthelion on 2006-11-06
>  	I'm a new Ubuntu user and just installed 6.06 yesterday, intending to create a dual-boot system. My current partition setup, according to GParted, is that I have one partition that contains Ubuntu and another entirely separate partition that contains two other partitions within it, one with my Windows XP data in it and one designated as a linux swap point. I can't, at current, get to XP from startup, as it's not one of my options listed in Grub, and GParted won't let me change any aspects of my current partition setup. How can I either edit my current setup or somehow obtain access to Windows XP?


Hi and welcome to Ubuntu

Your question isn't really clear:

Do you mean that you can't start up Windows, or do you mean that you can't acces your NTFS partition when you started up in Ubuntu

If you mean that you can't acces your NTFS partition when in Ubuntu, then please post the content of this file:
```
sudo gedit /etc/fstab
```

If you mean that Windows isn't in your grub list, you can check your grub list in menu.lst:
```
sudo gedit /boot/grub/menu.lst
```

You can add Windows there manually, or, if you don't know how, you might want to look to [this link]("http://www.ubuntuforums.org/showthread.php?t=293558&highlight=reinstall+grub"). 

Hope this helps,

Ecthelion

---

### Post by turtlewars on 2006-11-11
> title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

This is the code that the file you requested produced; I'm unsure as to what to do with it or what any of it means.

---

### Post by Ecthelion on 2006-11-12
Alright so windows isn't in the grub list...

What is the name of the partition windows is on?
(this should be something like /dev/hda1 or /dev/sda1 or something like this...)

---

### Post by seshomaru samma on 2006-11-12
you need to add a windows option to the Grub menu (the one you just posted)
in order to do that you need to know the name of the Windows partition . You can find it with fdisk
please post the content of :
```
sudo fdisk -l
```

---

