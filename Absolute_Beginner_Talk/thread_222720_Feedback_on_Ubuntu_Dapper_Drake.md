---
title: "Feedback on Ubuntu Dapper Drake"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by MilesTeg on 2006-07-25
Hi

I've just completed my personal goal to get Ubuntu + Quake 3 up and running :)

Just want to give you an idea where I see problems with the way beginners have to deal with linux.

about me: I'm a german windows user since 3.1 / MS Dos. My knowledge of linux is very basic and I never tried it for more than some days. 

Hardware: Laptop "acer Extensa 4100". centrino, ATI X700 mobility


getting started:
well. I first tried xubuntu - nothing happens - black screen. The same with Ubuntu. After a googling I found [http://wiki.ubuntuusers.de/Acer_Extensa_4101WLMI](http://wiki.ubuntuusers.de/Acer_Extensa_4101WLMI) 
Seems it doesn´t recognized the monitor correctly.
I followed the instructions and YES it worked.

After that installation was a breeze. I installed ubuntu beside my current windows partition.

For the configuration I used Easy Ubuntu, wich was a BIG help! It nearly installed everything I needed on my fresh OS. The menu is nice and userfriendly.

Now it gets complicated. Installing quake wasn´t that easy because I needed to know about sudo and how programs work with it. Some dirs wouldn't allow me to copy certain files.
Well, in the end I used a tutorial that I could just copy n paste, command after command.
Also Firefox wouldn´t connect to the idsoftware ftp directly (I needed the 1.32 patch) so I had to use nautilus. Seems somehow FF in linux can't handle log in ftp dirs??

After another long copynpaste tutorial I got q3 installed. A icon appeared in my start menu (or however you call it in gnome) but it didn't do anything. I tried using the Administration Terminal and entered "quake3" and the console really starts!

First error: opengl doesnt start. seems Easy Ubuntu didn't install the ATI drivers as I had expected.
So I used another manual ([http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)) to install the newest drivers - you know, copy n paste.

Now I could see quake 3 in all it´s open sourced glory!
well, but I couldn't hear it. I installed some kind sounddriver of sounddriver but I got the msg 
"Could not mmap dma buffer PROT_WRITE|PROT_READ"
I googled again and another cryptic command found on [http://www.happypenguin.org/show?Quake%203%20Arena&start=10](http://www.happypenguin.org/show?Quake%203%20Arena&start=10) helped me (echo "quake3.x86 0 0 direct" >/proc/asound/card0/pcm0p/oss).

In the end everything worked, but I'm a bit frustrated on how heavily you have to rely on the console to actually change something in the system. More menus like in Easy Ubuntu would be much more userfriendly.

A BIG THANKS for the tutorials, they helped a lot :)

---

