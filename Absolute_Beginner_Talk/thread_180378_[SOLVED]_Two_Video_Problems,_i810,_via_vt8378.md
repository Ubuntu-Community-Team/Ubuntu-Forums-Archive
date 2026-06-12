---
title: "[SOLVED] Two Video Problems, i810, via vt8378"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by argie on 2006-05-22
The Intel i810 first:
I can't open a linux GUI on this computer though it runs Windows fine with the same settings (60 Hz, 800x600, 16 bit), and I even tried the xorg reconfigure thing with dpkg-reconfigure. 
The problem also happens with RedHat Linux, which doesn't even manage to open its installer.
The screen looks like stripes or lines of different colours, and sometimes the Ubuntu screen flashes for a second at a low resolution. (I recognise it because Ubuntu works on this computer)
If it's any good, here are the specs:
Intel Pentium III Celeron 1GHz
82810E Motherboard
Graphics is onboard
RealTek 8139 Ethernet card
128MB RAM 
40GB Samsung harddrive 
That's about all I know now, but if you want any specific information I'll look around.

Now the via:
This is the one I'm posting from. Everything runs fine for normal use, but certain games and applications are super-slow. 
*glxgears -printfps*
173 fps
The games that I have trouble with are cube and scourge. A game I've got that's managed to run smoothly is OpenTTD. I'm not sure where the problem is, but I think I don't have proper drivers.
The thing is I read somewhere that the original via drivers on the via site are really bad, and I don't want to install them and mess up this Ubuntu setup because I've grown to really like it and have stuff that I don't want formatted in a reinstall.
So I just want to confirm that the video card is the problem. Then I'll proceed getting some drivers.
And by the way, if the newer drivers will be included in Dapper in June, I'll wait.

Also, thanks to everyone who helped me in the other thread ^^

EDIT: For the via, if you don't get direct rendering, reduce your colour depth or resolution.

---

