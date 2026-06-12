---
title: "[SOLVED] External Drive"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by nikRbokR on 2008-02-18
I tried to install Gutsy on my external hard drive using my laptop.  I followed the directions that it gave me in the book "Ubuntu Hacks" by O'Reilly.

I used the text based installer.

I made sure to install ubuntu on the external HD @ the partitions point .
I made sure to install GRUB on the external drive as well:
```
/dev/sdb
```

However, it says that before hitting continue, I had to do Alt+F2.  Then, I needed to do
```
# mount -t proc /target/proc
```

*Got an error message here (something about couldn't find /etc/fstab ?)*

then do
```
# chroot /target
```

then once inside the chroot environment, do
```
# vim /etc/mkinitramfs/modules
```
*I tried to do this by skipping the previous steps, but it gave me a lot of blue "~" on the left side*

I have no idea what to do!  I'm willing to go through the installation process again if it means that I can FINALLY get to use Ubuntu.

I've had a lot of trouble trying to install Ubuntu to my external drive.

The drive is a:
Western Digital "Enhanced IDE Hard Drive", 30GB.

It's kinda old and the external drive equipment is kinda crappy as well.  However, it all seemed to be working, until then!

On  a side note, by not editing the modules, when I hit continue and the laptop rebooted, it told me that it couldn't mount the drive, so I'm using XP right now (on my internal hard drive).

THANKS!!!

---

### Post by nikRbokR on 2008-02-18
I had tried using the Live CD w/o the internal hd in the laptop, but it gave me a kernel panic message, so I tried it this way.

---

### Post by Fred_E _krugar on 2008-02-18
You may already know this but make sure in the bios boot from usb device is on.

---

### Post by smartboyathome on 2008-02-18
Try using [this guide](http://ubuntuforums.org/showthread.php?t=678146) to do it. I got Gutsy installed on an external HDD using it.

---

### Post by nikRbokR on 2008-03-23
That was a perfect guide.  I had a little bit of trouble w/ the commands to edit (w/ nano)  but it was easily solved by adding 'sudo' in front.

---

