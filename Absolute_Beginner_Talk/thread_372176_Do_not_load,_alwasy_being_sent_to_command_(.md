---
title: "Do not load, alwasy being sent to command :("
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by teft on 2007-02-27
hi

this is my problem:
I installed the ext2 driver to share files between windows and ubuntu, also, I have ntfs-3g in ubuntu, so I decided to uninstall ext2 driver...I've restarted my pc and tried to load ubuntu but I just do not complete the load bar, in fact I loads only 10% of the bar, then I go to command interface and this error came up

```
/bin/sh: can't acces tty; job control turned off
```

can I fix it with any command? I tried looking in the list of aviable commands but I dunno what to do

thanks

---

### Post by xyz on 2007-02-28
Try this:
> ALT + CTRL + F1
```
sudo dpkg-reconfigure xserver-xorg

```
so as to to configure manually your settings for the X enviroment, graphical mode.
Put in the correct information and reboot.

---

### Post by urk_nono on 2007-02-28
You might need to install the xserver if it says xserver is not installed. That's what happened to me..

**sudo apt-get install xserver-xorg**

---

### Post by teft on 2007-02-28
thank you!! Ill try and Ill tell you if I can fix it xD

---

### Post by teft on 2007-02-28
well... it didn't really help but thanks... I pres ctrl+alt+F1 and it says that cant find /sbin/init in the filesystem... maybe its not there xD How can I get it back? :D

thnx

---

### Post by xyz on 2007-03-01
I found this on the site. It was posted by [i]Rongo_Tai
[/i]
>  Re: /bin/sh: Can't access tty; Job control turned off
See
[http://www.google.com/search?hl=en&n...+off&spe ll=1]("http://www.google.com/search?hl=en&n...+off&spe ll=1")
for solutions to this problem from a number of sources, including Gentoo lists.
It's fairly common, apparently. Basically, the kernel needs a ramdisk bigger than 4096 at boot. Setting it in grub.conf or lilo.conf to 8192 apparently fixes the problem.
Eg 'ramdisk_size=8192' or 'ramdisk=8192' .

If you are stuck at BusyBox just boot via [Ubuntu ?] LiveCD, follow the documentation to mount your root partition, boot partition, and proc (?), then chroot and edit the conf. System should then boot.

An example of a working /boot/grub/grub.conf ..

-------------------------------------------------------------
default )
timeout 15
spalshimage=(hd0,6)/grub/splash.xpm.gz

Title=Ubuntu Linux
root (hd0,6)
kernel /kernel-2.4.26 root=/dev/ram0 init=linuxrc ramdisk=8192 real_root=/dev/hde9
hda=ide-scsi hdb=ide-scsi
initrd /initrd-2.4.26

Title=XP
root (hd0,0)
chainloader + 1
------------------------------------------------

Rongo_Tai
Reply With Quote

---

### Post by teft on 2007-03-01
Thank you... but I realized that my problem is that ***/sbin/init*** is just not there and I dont know what to do... should I copy anoter one and put it in the sistem? I have the live cd of ubuntu drapper but I dont have a backup of this file, is it different in the 6.10 version? The boot error is because of that, it cant find that file... any ideas

thanks

---

