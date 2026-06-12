---
title: "Won't detect my drivers"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by sumsimpleracer on 2008-03-02
To start off, i'm an absolute beginner at linux and i heard ubuntu is the one i should try if i'm converting from windows, i've used windows all my life and i want to try something new

I set up my computer, still a work in progress seeing that everything is not in a case, instead sitting on a box and i'm using an old hard drive that originally had windows ME...the most worthless OS ever created

but anywayz my set up so far is:
MB: nVidia 680i LT
Video card: 8800GS
Processor: Intel Quad Core
Memory: 4gb OCZ DDR2

but anywayz...since i'm using an old HD and reformatted it to use ubuntu because it takes less space (i'm using a 20gb harddrive) I gave it a shot at downloading the drives...i quickly learned that Windows and Linux download completely differently (this is before i started reading a guide i found on this forum) But even after reading a guide, i still don't understand how to download and install my drivers.

Can anyone help me?

I thought i had it set up at one point. I pressed alt+F2 and typed in the file it should run. I guess it worked because it was able to detect it and everything and my resolution was no longer 800X600. 

But heres the biggest problem. I logged out because the computer said "all users must logout to be able to see changes" or something to that effect, when I logged back in, it said i was in low graphics mode and i had to configure it manually and whaddaya know...none of my stuff could be detected anymore...

I just don't want my Video Card or anything else for that matter running at 100% if it's just running mozilla

edit- i'm using gutsy gibbon if that helps at all

---

### Post by jan quark on 2008-03-02
try to reconfigure your xserver with this command
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by paydaydaddy on 2008-03-02
Lots of good stuff on psycocats page. follow this link and read about enabling extra repositories and installing nvidia drivers as well as lots of other useful information.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by sumsimpleracer on 2008-03-02
Quark this is what it says after typing your advice into the console
> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080302154218
also payday...i looked at the site and followed it's directions, and it says that i should try to access the restricted drivers managers but this is what it says
> Your hardware does not need any restricted drivers.
so...what do i do now...so i think it's just not detecting my hardware

---

### Post by sumsimpleracer on 2008-03-02
sorry for double posting...but

incase it may help this is what it says 
> bryan@ubuntu:~$ sudo aptitude install NVIDIA-Linux-x86-169.12-pkg1.run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "NVIDIA-Linux-x86-169.12-pkg1.run"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      



so i have the file that it claims it doesn't see saved on my desktop...where should it be for it to be detected

edit-so...i checked the cd that my card came with and it only offers stuff for windows OS's...and i checked online at XFXforce.com for the drivers but it only offers for windows...but seeing that it's made by nVidia, then i should just download the drivers from nVidia right?

editX2- so i think i found my problem...after reading the appendix of supported video cards by nVidia...they don't list out the 8800 GS but i think that's because it's so new because they don't support the new 9600 either

---

