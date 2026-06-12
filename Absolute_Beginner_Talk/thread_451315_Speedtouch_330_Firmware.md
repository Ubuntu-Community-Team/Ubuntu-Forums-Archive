---
title: "Speedtouch 330 Firmware"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by hightails on 2007-05-22
I have just downloaded and installed my first Linux boot - Feisty. I have set it up to dual-boot with Windows 2000 until I have fully checked out what Feisty can do.

One of my first hurdles has been that in order to get my USB Speedtouch 330 modem to work I am advised to install a firmware update.

Will this affect it's operation with Windows 2000?

I intend to switch to Linux one day, but I'm nowhere near ready to lose my Win2K internet connection yet!

---

### Post by jrusso2 on 2007-05-22
Flashing the firmware should not harm your modem but its important to follow directions exactly. YMMV things can go wrong.

---

### Post by hightails on 2007-05-31
Sorry to be so long coming back, but I have been comparing Ubuntu and Mandriva as my first ventures into Linux.

The bottom line is that I have managed to make the USB modem work in Mandriva using the method on [http://www.linux-usb.org/SpeedTouch/mandrake/index.html](http://www.linux-usb.org/SpeedTouch/mandrake/index.html). Unfortunately, I have not yet managed to get the equivalent process for Ubuntu to work.

For the benefit of other newbies, I have at least managed to find out more about "flashing the firmware". In actual fact, this process is not like a normal firmware update, in that it does not modify the modem in any way. It's more like an extra driver, which is installed on the hard drive and loads when the PC is booted. When you shut down, it is unloaded, which is why jrusso is right - it leaves the modem unaltered and perfectly OK to boot Windows (or anything else) as normal.

If anyone has any ideas about how to make it work in Ubuntu, I would be pleased to hear - otherwise I will have to stick to Mandriva and other as yet untried distros. Shame to throw Ubuntu away over one piece of hardware.

---

### Post by Rui Pais on 2007-05-31
hi,
check this:
[USB ADSL Modem Manager for Gnome]("http://ubuntuforums.org/showthread.php?t=445701")

general info/suggestions/howtos:
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)


good luck

---

### Post by hightails on 2007-06-02
Fixed!!!!!!

Thanks for the ideas, Rui Pais. Your second link is the one I've been using without success. Your third link is a very similar process, which didn't work for me either.

Your first link, however, worked first time for me. So now I am up and running. It's an installable program for Speedtouch 330 modems written by StevenHarper. I used his version 0.4.8.

I suggest anyone reading this passes this one on. I spent hours on this problem before Rui Pais pointed me at this simplest of solutions. 

Thank you for your help.

---

### Post by Rui Pais on 2007-06-02
> **hightails said:**
> Fixed!!!!!!

Thanks for the ideas, Rui Pais. Your second link is the one I've been using without success. Your third link is a very similar process, which didn't work for me either.

Your first link, however, worked first time for me. So now I am up and running. It's an installable program for Speedtouch 330 modems written by StevenHarper. I used his version 0.4.8.

I suggest anyone reading this passes this one on. I spent hours on this problem before Rui Pais pointed me at this simplest of solutions. 

Thank you for your help.

Hi, don't thanks me, i just point some directions (i suffered for a while too a few years ago when i had those kind of equipment...). 
Drop a word of encouragement to StevenHarper, his the brave one :)
and with that kind of project is good to know people use it and when it works.

have fun.

---

