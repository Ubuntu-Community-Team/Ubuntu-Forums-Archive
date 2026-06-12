---
title: "Dual booting.."
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by NeonBlue on 2006-05-26
And my computer gives me no chance to change boot order or anything when booting up, it auto boots to Windows.  Anyone know how I can change it to boot to Ubuntu?

---

### Post by confused57 on 2006-05-26
First of all, it's probably a good idea to try the LiveCD before attempting to install.

The bios in some older computers do not allow booting from the CD drive, if that is the case for you, you can create a SmartBootManager floppy disk, which will allow you to boot from the SBM floppy then choose to boot from the CD drive:

[http://ubuntuforums.org/showthread.php?t=142716&page=5](http://ubuntuforums.org/showthread.php?t=142716&page=5)

That's the first thing you might want to try, once you're able to boot from the CD, don't install until you've read some guides on dual-booting. 
For Dapper:
[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

For Breezy: 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Before attempting to install Ubuntu, make sure you defrag your Windows, makes resizing the Windows partition much easier for the Ubuntu installer.

You were indeed clear, I just misinterpreted it...You'll have to edit your /boot/grub/menu.lst default...I believe Lord Illidan is leading up to that...

---

### Post by NeonBlue on 2006-05-26
Apparently I wasn't clear.  I wiped the HD, partitioned, installed both Ubuntu and Windows and booted up both.  I'm now on Windows, but I don't know how to swap the boot order to get onto Ubuntu.

---

### Post by Lord Illidan on 2006-05-26
You mean that Windows is booting automatically, without giving u a chance to chose Ubuntu?

---

### Post by NeonBlue on 2006-05-26
Indeed.

---

### Post by Sgood1971 on 2006-05-26
If you see the word "Grub" on the screen when you first turn on the computer, press 'ESC' and you can choose Ubuntu from there. If you want to change the boot order, you will have to edit /boot/grub/menu.lst

---

### Post by NeonBlue on 2006-05-26
No Grub on the screen and I'm on Windows and not Ubuntu.  The point is that it automatically goes to Windows without showing anything else.  Windows is on a 9.5 GB partition and Ubuntu is on a 10.5 GB partition.  It's automatically going to the 9.5 GB partition.

---

### Post by Lord Illidan on 2006-05-26
You have 2 harddrives or 2 partitions on 1 harddrive?

---

### Post by NeonBlue on 2006-05-26
One HD, two partitions.

---

### Post by niviche on 2006-05-26
Did you install XP *after* installing Ubuntu?

---

### Post by NeonBlue on 2006-05-26
98, and yes.

---

### Post by niviche on 2006-05-26
Then I guess Windows erased Grub, which you have to reinstall. I don't know how to do it, but I guess somebody else on this forum can tell you what to do.

---

### Post by aysiu on 2006-05-26
[Restore Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113).

---

### Post by NeonBlue on 2006-05-26
Don't know how it'd erase it, it's on a different partition.  The real problem with restoring grub is that when the disc is in the tray, it still just goes straight to Windows.

---

### Post by benblur4 on 2006-05-26
That is a good question.  If you don't install Ubuntu last then Windows will automaticaly boot.  You must install Windows and then Ubuntu.

---

### Post by Lord Illidan on 2006-05-26
[quote=NeonBlue]Don't know how it'd erase it, it's on a different partition.  The real problem with restoring grub is that when the disc is in the tray, it still just goes straight to Windows.[/quote]

Then the problem is with your BIOS. Change it to boot from cd..

Generally, you have to press DEL at boottime... 

Not all bioses are the same, though.

---

### Post by benblur4 on 2006-05-26
The computer will usualy tell you to press "blank" button to enter setup.  Or something like that.  blank being F2, or DEL. etc.

---

