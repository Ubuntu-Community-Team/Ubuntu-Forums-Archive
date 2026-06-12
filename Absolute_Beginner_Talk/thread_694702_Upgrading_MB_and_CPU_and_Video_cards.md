---
title: "Upgrading MB and CPU and Video cards"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2008-02-12
Ok here is what I am going to attempt and need some advice, I upgrading two computers, both have XP home with SP2 installed but one is a dual boot with Ubuntu 7.04. I used to do this with 98SE and never had much problem. From what I have read the XP only box I will just boot to the cd and repair the install, is this correct? The dual boot system I can remove the Ubuntu drive and do the same with it, is this correct? Then reload the Ubuntu drive and have grub repair itself , is this correct? And through all of this I should lose no data correct? I am currently backing up all pictures and important files. This would not worry much except on both boxes the motherboard chipsets and different than what is loaded. Any advise and help would be greatly appreciated.:confused:

---

### Post by smartboyathome on 2008-02-12
I think you would be safer if you reinstalled everything. Especially with Ubuntu, your video card and such could crash the whole system since it uses different drivers than what is installed. I would do the same with XP as well.

---

### Post by ptn107 on 2008-02-12
All your hardware devices are remapped in the /dev folder every time your computer boots (which is contrary to Windows where that information is stored in the registry).  So regenerating this information is as easy as restarting your computer.  However, the configuration for your video card and drivers are stored in /etc/X11 and /lib/modules (or /lib/linux-restricted-modules).  I would back up your video configurations.  Everything else should be ok.  The previous post has a point though, after major hardware changes it is best you just back up your data and do a clean install.

---

### Post by LowSky on 2008-02-12
ubuntu should be ok. i have installed it on hard drive in one computer and then put the hard drive into another, as long as you dont install the video drivers you whould be fine. as for windows xp.. good luck.. i reccomend a clean install as my "repairs" have never turned out OK.

---

### Post by jhenager on 2008-02-12
Good advice above. I added a video card to my system this morning and got an X-server error. I had to run sudo dpkg-reconfigure xserver-xorg to get back into graphical mode. 
When you replace that much hardware, think of it as reaching down and yanking on the rug you are standing on. If you don't care about the data on the system, no problem, but my opinion is that there is no such thing as too many backups!

---

### Post by J11Gyro on 2008-02-12
Agreed on the backups but question I have to ask is this, since all my video cards nvidia and cpu's are amd the only thing really changing are the chipsets, and the CPU sockets, still a major problem?

---

### Post by J11Gyro on 2008-02-27
Ok got new Graphics intensive system built and ready to go, back up all on main box so am now ready to rebuild the dual boot box. As I said before all that is changing is motherboard and chipsets with it and CPU 2400XP to 3400 Sempron64 and going from a 5200 geforce to a 5500 geforce. Is there a way I can do this and just repair grub on start up or is there a repair update option in 7.04 Fiesty?

---

### Post by J11Gyro on 2008-02-27
Any Ideas other than total reload?

---

### Post by igknighted on 2008-02-27
> **J11Gyro said:**
> Ok got new Graphics intensive system built and ready to go, back up all on main box so am now ready to rebuild the dual boot box. As I said before all that is changing is motherboard and chipsets with it and CPU 2400XP to 3400 Sempron64 and going from a 5200 geforce to a 5500 geforce. Is there a way I can do this and just repair grub on start up or is there a repair update option in 7.04 Fiesty?

With such minimal changes, I doubt ubuntu will have any issues.  No "repair" mode or anything.  As for WinXP... that will likely void your OEM license, leaving you the option of pirating it or buying a new copy.  If repair works, you're in luck.

---

### Post by J11Gyro on 2008-02-27
Last time I had to do this if I remember right I repaired the XP load up and it went ok, just had to reactivate which is no big deal. What I am wondering is if I can take the Ubuntu HD out and just put it into existing case with another install of XP and have it pick everything up and do grub repair?

---

### Post by J11Gyro on 2008-02-28
I just had a thought, I have a system that has only had windows loaded to it XP SP2. Can I take my existing Ubuntu 7.04 Hard drive and move it that system and install grub without reloading?:confused:

---

### Post by J11Gyro on 2008-02-28
Any takers on this one  if not I will let you know how it turns out

---

### Post by jpdamigaman on 2008-03-07
HI I have upgraded mobo and cpu but kept HD and graphics card.

I tried installing new chipset drivers before my final shut down of xp pro but didn't quite work as I had to do a repair and re register windows.

I have tried to get ubuntu to boot to no avail!

It won't even boot off a live cd!

jpdamigaman-

---

### Post by jpdamigaman on 2008-03-07
Problem solved 

Graphics card radeon 9800 pro was in compatiable with MOBO!

---

