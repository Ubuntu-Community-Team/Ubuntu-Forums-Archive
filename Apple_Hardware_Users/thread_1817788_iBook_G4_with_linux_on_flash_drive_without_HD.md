---
title: "iBook G4 with linux on flash drive without HD"
date: 2011-08-03
forum: Apple Hardware Users
---

### Post by zacaj on 2011-08-03
Hi,
Ive got a iBook G4 with a bad harddrive, and instead of buy a new one (expensive), I just installed Ubuntu on a flash drive, and everythings fine.  The problem is that the bootloader is still on the harddrive, which means that I can only boot the system when the hard drive decides to work(under 50 degrees fahrenheit), so whenever I turn it on I have to leave it in the fridge first.  Is there a way to put yaboot, or some other bootloader on the flash drive and get the mac to boot it directly, bypassing the HD?

---

### Post by rsavage on 2011-08-04
Don't think so.  You coud put it on a cd?

---

### Post by rsavage on 2011-08-04
Also, you do know you can boot a USB device from openfirmware don't you?
 
Hold down o and f and command and option while turning on, then type
 
boot [EMAIL="usb0/disk@1:2,\\yaboot"]usb0/disk@1:2,\\yaboot[/EMAIL] 
(or something similar like 'boot usb1/disk@1:2,\\yaboot')

---

### Post by rsavage on 2011-08-04
Btw, the above post is assuming that you've installed the bootloader to flash. The only way to actually boot it though would be through openfirmware.
 
**EDIT: Correcting my own advice here! The above is not true. I was only repeating advice that I had read many times, but it turns out it was not correct when you look into it.**

---

### Post by zacaj on 2011-08-04
That OF command doesnt seem to work.  It says it cant open device or file.  What are the 1:2 supposed to mean.  The booting from CD is a good idea though...  Is there any way to make a cd that will just boot the flash drive?

---

### Post by rsavage on 2011-08-04
Those commands were taken from this thread [http://ubuntuforums.org/showthread.php?t=780320](http://ubuntuforums.org/showthread.php?t=780320) . It is assuming there is a bootloader partition on the flash disk like I said before. Have you made one? The numbers/command will change depending how you've got your flash disk setup and what usb port it is plugged in. That I'm afraid is for you to work out, but there is lots of info on the web to help you.
 
I think it should be possible to make a CD to do what you want although I've never done it. It would be noisy though until you eject it or power it down somehow. Try starting with a minimal install cd ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) and see how it is set up. Then possibly it is just a case of substituting in the bootloader files you have on your hard disk? I don't do alot with burning cds I'm afraid so can't help you much.

---

