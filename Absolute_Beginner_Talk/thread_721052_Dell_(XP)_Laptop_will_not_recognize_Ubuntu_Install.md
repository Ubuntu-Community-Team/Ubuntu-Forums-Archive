---
title: "Dell (XP) Laptop will not recognize Ubuntu Install CD"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by mikeypox on 2008-03-10
I am brand new to Linux... 

I burnt the newest Desktop release of Ubuntu on to a CD using the ISO provided on the Ubuntu website. I have used two different ISO burners, Nero, and ISO Recorder. My work computer recognizes both of the Ubuntu CDs with no problems (I can not install Ubuntu on my work computer), but my personal Dell laptop (Inspiron 5100) treats them as blank CDs. Any ideas?

---

### Post by DUDE_2000 on 2008-03-11
With most laptops you have to configure the bios to get it to boot from a cd

reboot you'r computer, and there should be a screen with a dell logo and a grey bar at the bottom, on that bar it sshould say things like "hold F12 to change settings"

press the button (usually F10, or F12) and search the cmos menus for  options like " hold F12 to open boot menu" or "change boot order"

Change the boot order to your cd drive first, or enable the menu, and select your cd drive from the list. that should get it to boot

---

### Post by LieToPurify3 on 2008-03-11
When you say it treats them as blank CD's, do you mean that you put it in the tray, tried to boot up with the live cd, and your laptop just booted up into Windows normally and ignored the cd?  If so, make sure your BIOS is set to boot from cd before it boots from your hard drive.  I't's different for a lot of mobo's but try holding F1 during startup; that should get you to the BIOS screen and you can set your boot priority from there.

Ah sorry, I guess we posted at the same time.

---

### Post by paydaydaddy on 2008-03-11
Have you tried another cd to make sure the cdrom in the laptop is working properly? Do you have the bios set to boot from cd? The basics, I know, but yjou gotta start somewhere.

---

### Post by DarinB on 2008-03-11
The question is not only if you are set up to boot from the cd  first it is???
What does the computer do when you boot up with the cd in?? does it ignore it and not even light up at boot up??? do you have two  drives one dvd followed by a cd i have that and my boot up is the dvd  not the cd. let up know??

---

### Post by mikeypox on 2008-03-11
Yeah, I have tested my CD Drive with other discs, it does work. The problem is that it will not recognize the CD as a valid disc, even from within Windows. 

The BIOS is set to load from CD first, and the CD drive light does turn on before Windows starts to load. 

I am thinking it may be a similar problem to my Compaq desktop that has some sort of hardwired copy protection that refuses to load burned ISOs.

---

