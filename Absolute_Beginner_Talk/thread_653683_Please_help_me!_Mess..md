---
title: "Please help me! Mess."
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by ftaylor on 2007-12-30
I had everything on my Ubuntu Gutsy installation working perfectly, compiz fusion, fglrx drivers for my radeon mobility card smooth, sound, wireless... everything. I tried to install the ATI driver for the card as I was trying to get CS Source to work on ubuntu. It appears as though it modified Xorg and all the eye candy and graphics started going really slow. 

I tried to revert back using sudo dpkg-reconfigure -phigh xserver-xorg and managed to get the graphics working quickly again, but without the eye candy. I tried playing about to fix this with various configurations and now it wont even load the login splash screen: it just stays black.

I've been doing all these fixes with recovery mode, then typing exit when finished which prompted the booting of ubuntu. The last time I was doing this it took me to command line boot - there were no graphics, but I logged into my profile with text. I think I made a big mistake by typing "sudo shutdown now" which then told me that ubuntu was going into maintenance mode - now when I type exit from recovery mode it just says "recovery mode ended with status 1" and ubuntu doesn't even attempt to boot.

All I really want to do now is grab some essential files - like my bookmarks from firefox, and some java programming. Can someone please tell me how to get ubuntu out of maintenance mode? I'm just going to reinstall it once I've got the files I want.

Any help appreciated.

Sorry for the mess.

---

### Post by laidback on 2007-12-30
If I was in your shoes I'd try booting from the Ubuntu Live Cd, or some other Live system like Knoppix, in an attempt to access your hdd so that you can copy the files you want onto a memory stick or usb hdd.

---

### Post by ftaylor on 2007-12-30
Yes, I was thinking that. So booting from live cd will take me to my files?

---

### Post by Sef on 2007-12-30
> If I was in your shoes I'd try booting from the Ubuntu Live Cd, or some other Live system like Knoppix, in an attempt to access your hdd so that you can copy the files you want onto a memory stick or usb hdd.

I have used [Knoppix ]("http://knoppix.com")for moving files from hard drives that would not boot up to usb key and had no problems in doing so.

---

### Post by ftaylor on 2007-12-30
Ok, thanks very much folks. I'll try that.

---

