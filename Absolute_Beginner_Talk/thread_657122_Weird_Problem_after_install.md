---
title: "Weird Problem after install"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2008-01-03
Hi,

I am sure whether this has been asked before. I searched some of the threads but couldnt find a solution to my exact problem. I recently installed Kubuntu 7.10 on my friend's IBM Thinkpad (40Gb, 1Gb). I used the Guided partitioner provided by the installer. Currently this laptop is not able to connect to the internet. After install, rebooted the machine. It says grub is loading and starting and thats it. The screen goes blank and I have to restart the computer.

During the next reboot I went into recovery mode and forced kdm to start and it started without any problems. I was able to log in to the desktop. This told me that X had not crashed. However, I rebooted the machine again and when I seclet Linux-generic instead of recovery on the grub menu, the same thing happens. The screen goes blank and nothing happens. 

I would appreciate any help on this.

Thanks.

---

### Post by pointone on 2008-01-03
Try booting with the noacpi boot option.

---

### Post by PPAAUULL on 2008-01-03
You could switch to the command mode on the normal bootup to see if anything is starting up I think you can hit esc after you choose what ever you want in grub.

---

