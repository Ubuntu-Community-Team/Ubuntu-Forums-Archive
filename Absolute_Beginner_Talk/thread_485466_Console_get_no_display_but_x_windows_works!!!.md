---
title: "Console get no display but x windows works!!!"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by stephenlittleton on 2007-06-26
Hey all, 

I am using feisty on a Pentium 4, 2.4 GHz 512mb, ATI Rage 128 Pro with 200gb SATA drive.  The board is ASUS P4S8X.  

When i installed ubuntu, i installed UBUNTU SERVER and APT-GOT everything else.

I installed from the console, and rebooted, and it started x windows no problem.  I now have opengl support, and the screensavers now look like they are supposed to, for instance, instead of the matrix screen saver just ticking down one charecter per 2 seconds, it now floods the screen and shows the different pictures.  Amazing.  I still cant get beryl to work, but COMPIZ seems to load no problem. 

SO I COMPILE my kernel, and deselect all the drivers for the hardware i dont have... left a lot I did not know about alone and at its defaults...

--- Now ever since then, I have not been able to see my console or even kill x and have a console login.  The monitor just kinda shuts down as if its off, cause I have an old 17" CRT... but it did it when I had a 19" LCD, so I dont think its the monitor..

I am almost positive I did something during the compile, but what?  What would cause the console not to work but x windows to work.....

Bet this is a first, most the time people complain about getting x to work, i am complaining about the exact opposite!  :D

Thanks for your help in advance.

](*,)[-o<

---

### Post by charles.g.moore on 2007-06-26
I had the same problem with my laptop.  I am assuming that when you alt-f1,f2,f3 etc. you get a black screen...

In order for me to fix it I had to turn off the ubuntu startup splash screen and it gave my tty sessions back...

[http://ubuntuforums.org/showthread.php?p=2585748](http://ubuntuforums.org/showthread.php?p=2585748)

---

### Post by stephenlittleton on 2007-06-29
I think you are on the right track but its ubuntu logo that pops up.  This being said I use kde and have installed ubuntu-desktop kde, then kubuntu-desktop.  If i could only find a way to disable the login screen for kconf-editor if there is such a thing... or an ubuntu editor, like linux used to have "configurelinux" or something to that effect, i bet it would be in there.

---

### Post by stephenlittleton on 2007-07-01
Its almost as if the default display driver is broken, and the only way drivers are loading is beacuse of the xwindows.  So maybe i took out default video driver support.  I get vid all the way until the grub menu, i can move around and select thing, as soon as I hit enter (and I have all the logos installed for grub... the bootscreens)  It just seems like its not loading until xwindows.  I am going to wipe this baby clean and reinstall and just not touch it... seems to be no change in speed... 

Now my little PII 266 server has feisty installed and compiling its kernel made one HECK of a difference  :o

---

