---
title: "Need help desperately(Recovery Mode)"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Andhraman on 2006-11-16
Hello everyone,

I installed Ubuntu 6.10 using Live CD on my Dell Inspiron 2650.  I have successfully installed Nvidia drivers.  I have been trying to get Ubuntu to recognize my wireless card for about a day.  I am not sure what happened but when I tried to uninstall ndiswrapper and re-install it something went wrong.  **X does not start anymore, the process bar(under Ubuntu logo) goes half way and then blank screen appears.**  Ctrl+Alt+Delete(old windows habbit) takes me to blue screen where it says X server could not start and login prompt comes up.  When I login, I can't edit any files(Read-only file system).

Recovery mode hangs also, after it reaches the following output:

[FONT="System"]* Loading manual drivers...
[17179594.340000] lp0: using parport0 (interrupt-driven).
[17179594.404000] ndiswrapper version 1.28 loaded (preempt=no,smp=yes)
_[/FONT]

Again I can get to command line in recovery mod with ctrl+alt+delete, but I can't edit anyfiles (Read-only file system).  I can not reconfigure X because of this also.  To add to these problems my CD drive stopped working.  So I can not use Live CD to boot.  ](*,) Does anybody have solution to this problem other than me buying a new CD-Rom drive?  I been reading forums and documentation to solve this for about 2 days now, any help is greatly appreciated.

Thanks.

---

### Post by SZorg on 2006-11-16
... I fail at reading.

And I can't delete this.


If you have another computer and a 256MB flash drive, put DSL on it and try to reconfigure X manually?

---

### Post by Andhraman on 2006-11-16
j

---

### Post by Andhraman on 2006-11-16
SZorg can you explain more in detail..put DSL?..how will this help..Thanks.

---

### Post by Andhraman on 2006-11-16
I think I should get some sleep and resume my negotiations and settlements with ubuntu tomorrow morning.  Solution to my problem is greatly appreciated from somebody.  Of all the brilliant minds out there I am sure somebody has the solution on the tip of their brain.   :D 

Thanks.

---

### Post by Mimsy on 2006-11-17
DSL = Damn Small Linux.

It can be set up to boot from a USB drive, like the live CD works, but from the flash key. Very handy, I'm sure, if one's computer is capable of booting from USB. Mine isn't. :(

/Mimsy

---

### Post by SZorg on 2006-11-17
If your computer'll boot from USB, on another box download and install DSL (Damn Small Linux, aforementionedly).

The site is located here:
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Install instructions here:
[http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive](http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive)


I couldn't tell you what your problem is -- I'm not that advanced either. That's where I would start for the diagnose & repair process.

---

### Post by Andhraman on 2006-11-17
No luck guys/gals.  I looked into this before, but I knew my laptop BIOs does not support USB boot.  These are boot options in my BIOs Cardbus NIC, Onboard NIC, Floppy Devices, CD-ROM Drive, Hard Drive.  But I tried it anyway just to be sure.  It didn't work.  :( Thanks anyway SZorg and Mimsy for suggesting.  Any other ideas, please?

Thanks.

---

### Post by doobit on 2006-11-17
Do you have a Floppy drive? DamnSmall can boot from a boot floppy that you can make from an image on their download site, and then run the rest from the USB drive.

---

### Post by anaconda on 2006-11-17
DSL has a boot floppy, which loads USB-drivers and then boots from USB.. So just make tho floppy, and boot from it.

And by the way 64MB USB-stick is big enough.. you don't need 256MB one. DSL takes only 50MB

I had to use that method with my old laptop. DSL can also install itself from the USB-stick to hd...

The only "problem" with DSL is that it is a bit harder to use than ubuntu, so you will have to mount your hd manually etc..

---

### Post by anaconda on 2006-11-17
Oh.. and if you dont have USB-stick..
There are also other small linux-distros, which fit completely to 2 floppies...

---

### Post by sinpalabras on 2006-11-17
hi, do you know how to use "sudo"?Sorry but may be the problem at recongfiguring x. By

---

### Post by Andhraman on 2006-11-17
I have floppy drive on the laptop which is the one with the problem.  But I dont have a floppy drive on the desktop from where I am posting this message.  Any other ideas?

Thanks.

---

### Post by Andhraman on 2006-11-17
hi sinpalabras,

I have tried reconfiguring x.  But the problem is at the end recofinguring it has to save the new xorg.conf. This is where my problem is, for some reason in both recovery mode and regular the entire file structure(hard disk) is "Read-only file system".  I can not edit, delete or create new files in any directory.

---

### Post by Andhraman on 2006-11-17
It looks more and more like I might have to buy a new CD-ROM drive to go with the laptop and boot from Live CD.  Does anyone have any other ideas?

Thanks.

---

### Post by Andhraman on 2006-11-17
help..anyone??

---

### Post by Mimsy on 2006-11-17
Library computers often have floppy drives, as do the ones in campus computer labs. Or you can borrow a friend's computer for a while? That's what I would do, in your situation. Alternatively, borrow a CD-drive for a little while.

Don't spend the money until you've exhausted all other options. ;)

/Mimsy

---

### Post by Shannon_VanWagner on 2007-10-20
Hi there, 

I installed Ubuntu 7.10 on my Dell Inspiron 2650 and enabled Nvidia GeForce Go proprietary drivers and after rebooting the screen either was blank, frozen, or sometimes would show some garbled output.

Here's what I did to fix it:

On bootup, hit F2 to enter the Dell BIOS
For the section marked "Video Display Device", switched the setting from "Simul Mode" to "LCD Mode"

Saved the setting with F10 and then exited and rebooted.


On reboot everything came up normal.

Go Linux!!

Hope this helps!

Shannon VanWagner

---

