---
title: "Big Install Problem!/ wtf wat the f*** happened here?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Thecoolguru on 2008-03-27
ok, so i was downloading ubuntu, la di da di da, right, so then I burn my pretty lil' iso to a cd, pop it into the cd player, reboot, select boot from cd, and <zomg>EVERYTHING WORKS PERFECTLY FINE!!! </zomg>
so then,  i go to install it. i didn't want a normal install, but I wanted to have an OS per drive (i have an external drive). so i go to install it to watever i knew was the external drive, cuz i forget now but i researched and asked a friend who has tried all top 100 linux distributions, and he thought i was doing everything right. so the install finishes, and i restart the machine/ take out the disk, and try to start up from the external drive. my comp couldn't find an os to run on. so i say, ok it was probably a bad install. ill just use crappy windows until i can use a more n00b friendly distro like linux mint or something like that. so i go to start from my c drive and again, nothing happens! i believe i had succesfully reformatted my disk without installing an os on it, but accidentally overwriting windows. now my dad won't let me switch operating systems again! :'(
right, so what the hell happened?

---

### Post by virtuallinux on 2008-03-27
Ok, lets see if we can diagnose the problem.  Put the CD back in the drive and boot to it again.  Go to Places > Computer.  It should open up the file browser and show you all of your disks.  Open up the one Windows is on (or is supposed to be on), and see if it looks like windows is still installed there.  My guess is that you've just got a problem with your boot loader/MBR.

---

### Post by Whiffle on 2008-03-27
First of all, your description is pretty hilarious.

Second, chances are you didn't overwrite windows (we hope), but you may have overwritten your master boot record, which isn't all bad.  What happens when you try to boot, with and without the external drive plugged in.

---

### Post by Joeb454 on 2008-03-27
Does your PC support booting from USB (e.g. the external drive)?

And if you open a terminal from a Live CD and run ```
sudo fdisk -l
``` (that's a lower case 'L') we can see if it's killed your Windows install :) Well...if you post the output back here we can anyway :p

---

### Post by cisforcojo on 2008-03-27
Yep, sounds like a boot from USB problem. Your windows partition is probably intact.
You can use the Windows install disk to fix your MBR.

This should do nicely: [http://www.techzonez.com/forums/showthread.php?t=3975](http://www.techzonez.com/forums/showthread.php?t=3975)

What you'll want to do is go into your BIOS and see if you CAN boot from USB. If not, you're not going to have any luck running Ubuntu from an external drive unfortunately.
Also of note, re: this problem, Linux Mint won't help you. I use Linux Mint right now and you'd also run into the same problem with it as well. 

If your BIOS doesn't support boot from USB, you can check for BIOS upgrades (be careful with this though).

---

### Post by Thecoolguru on 2008-04-27
I'm still not entirely sure what happened there, but I reinstalled Windows and clearly SOMETHING had worked because Most of my stuff was still there. Alas, no programs, but a lot of my important files. But now I'm running Wubi because I'm paranoid that I'll re-reformat my disk. Again. But everything seems to be going fine *except* for a slight networking problem and the fact that I can't find the CD that has the driver for my external drive... Just another day at the office...

---

