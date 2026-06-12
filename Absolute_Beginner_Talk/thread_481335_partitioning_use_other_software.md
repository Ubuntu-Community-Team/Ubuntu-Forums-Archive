---
title: "partitioning use other software"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by jhawk43 on 2007-06-22
Being all new to Ubuntu, I have a couple of questions.
1. I want to install ubuntu on an external hard drive. Can I use Acronis disk director to first partition my external hard drive?

2.Have seen several posts indicating that grub creates a problem when booting. How do I avoid this problem when installing ubuntu on my external drive?

Appreciate any comments.

---

### Post by coffeecat on 2007-06-22
Question 1 - Yes, absolutely. I've often used Acronis Disk Director to create partitions with Linux filesystems. It's a good bit of software. As an alternative you can boot up the Ubuntu live CD, plug in and switch on the usb drive which will be automounted by Ubuntu live, and then go into System > Administration > Gnome partition editor (Gparted) which will do an equally good job.

Question 2 - Grub doesn't cause problems when booting. After all, grub stands for **G**rand **U**nified **B**oot **L**oader. Problems with grub are usually caused by - um - how shall I put this - the person who was configuring it. :wink:

Grub is a relatively simple piece of code designed purely to boot various operating systems - and it does this very well - but it can't itself recognise a USB drive - it needs the Linux kernel for this. Grub calls the Linux kernel and than hands over to it. But if the Linux kernel is on the USB drive, well..... you get the picture. :)

However, the BIOS on **some** machines can recognise USB drives, and then grub can cope. But for machines where the BIOS cannot recognise USB drives you have to use a complicated workaround. [Have a look at this.]("https://help.ubuntu.com/community/BootFromUSB") Warning - it is not for the faint-hearted.

Do you want to avoid installing Ubuntu to the main hard drive? Are you concerned about certain booting issues that you seem to have come across? Be assured - and I mean this in the most respectful way - such problems are usually down to human error. However, they do occur. When I first started with Linux, and not having the confidence that comes with experience, I fitted a removable hard-drive caddy to my machine. If that interests you I can tell you more.

---

### Post by louieb on 2007-06-22
If you install Linux on and external and use GRUB as your boot manager you must realize the external drive must be plugged in every time you reboot. There are ways around this. By creating a boot floppy with GRUB on it or using the [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/")  or some other boot manager.  Lots of ways to do it. GRUB is the boot manager/loader of choice for Ubuntu because it is open source. 

To get some idea of the various ways check out the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by logos34 on 2007-06-22
> use GRUB as your boot manager you must realize the external drive must be plugged in every time you reboot. There are ways around this. By creating a boot floppy with GRUB on it or using the Super Grub Disk  or some other boot manager

You could indeed put it on a floppy (if you have a floppy drive), at least temporarily until you know it works...that's what I do initially to test it.  Best to use the Alternate Install CD and specify (fd0), although you can also hit the Advanced button at the bottom of the 'REady to install' screen on the live cd (Feisty) and specify (fd0) or /dev/fd0.  But afterwards why not put it on the MBR of the external USB?  You'll set the usb drive as first bootable hard disk in the BIOS, and the internal windows disk second, so if the usb is turned off/unconnected you will boot into the internal drive.  Simple.  You just have to edit /boot/grub/menu.lst and device.map afterwards.

---

### Post by carls on 2007-06-22
You say:

You'll set the usb drive as first bootable hard disk in the BIOS, and the internal windows disk second, so if the usb is turned off/unconnected you will boot into the internal drive. Simple. You just have to edit /boot/grub/menu.lst and device.map afterwards.

Ah, that's what I've been looking for. Would you be kind enough to go into a bit more detail about the edits needed?

(Context is a portable that will boot USB and Ubuntu will be installed on the external USB drive.)

Many thanks.

Carls

---

### Post by jhawk43 on 2007-06-23
All in all I would like to use Acronis OS selector when I reboot to select the drive or partition. Not sure what grub will let me do. Sorry for being such a dummie about this. Also when I install a partition what file system should I use when making this partition, i.e., NTFS or what.

---

### Post by Malta paul on 2007-06-23
I would suggest, EXT3 for your Linux files and Fat32 for your windows files. With fat32 you can read and write to the partition using both Ubuntu or windows with out problems.
Check this out [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) -great info.
Have fun :)

---

### Post by jhawk43 on 2007-06-23
I appreciate everyones input. Sure there will be other questions as i move along.

---

