---
title: "2011 Macbook Pro Boot Issues"
date: 2016-09-28
forum: Apple Hardware Users
---

### Post by tj.stine on 2016-09-28
Hello All!  I've been at this for about a week now and made a lot of progress, but I have become stuck.  I have a 2011 Macbook Pro with an i7.  Appears to only have Intel graphics.  I was able to install 16.04.1 Desktop by using nomodeset to boot the installer.  After finishing up the installation,  the machine rebooted to a blank screen (the screen is the sort of purple "ubuntu" color.  I got it to boot up properly by using nomodeset and I then edited /etc/default/grub to add nomodeset and ran update-grub.  Upon a reboot, I'm left with the same blank screen.  Now what seems to be the weird part.... If I enter grub before boot and either hit enter on the first (and only) option OR if I wait at the grub screen and let the 30 second timeout run down, it boots just fine.  It only boots up if I enter the grub menu first.   I have tried commenting out the 'quiet' lines in the grub settings and then it displays the grub screen on startup, but after making this change the system will not boot at all.  I've installed updates, formatted and reinstalled Ubuntu a few times..... still can't figure this one out.  Any thoughts??  THANKS!!

BTW Ubuntu is the only OS on this machine.  I have installed a new hard drive and it doesn't have OSX on it.

---

