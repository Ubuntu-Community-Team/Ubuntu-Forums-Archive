---
title: "[SOLVED] How to access a G3 hard disk (+Kubuntu) from an HP..."
date: 2008-12-03
forum: Apple Hardware Users
---

### Post by kudzugarden on 2008-12-03
Hello,

So I have a Power Mac G3 (blue and white) with Kubuntu 7.10 installed and lots of precious mp3s stored on the hard drive. The computer was in storage for a while, though, and now the graphics card doesn't work. How could I get the files off the disk?

I've tried booting the G3 and blindly logging in so I could ssh to it from another PC, but I can't seem to log in. I've also tried trading out the disk, but since it's formatted for PPC, my HP desktop won't boot from it; and when I boot from a live cd, I can't mount it (although it seems like I should be able to).

I've thought about adding it as a second hard drive to the HP, but the cable only allows for one. Is there a way to mount it as an external hard drive? 

I wonder if I could blindly boot the Mac from a live CD that would let me ssh or vnc into it... Is there a live CD for PPC that has vnc activated by default, or could I make one? Or is there an easier way to get to this music?

---

### Post by tiresia on 2008-12-03
I can imagine two easy solutions + a bit more complicated one.
1. easiest: plug your g3-hd in an usb external case. 
If you have Ubuntu on the HP desktop, you should see it in /media, or you can just mount it.
2. insert the g3-hd in your HP desktop and start it from a Live-CD. You can start gparted, to see if the Live-CD detected the HD and where it is mounted.
......
3. you could also start the g3 from a cd or from an usb memory stick and connect to it trough vnc, as you said. Here you can find some infos. 
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-usb-files.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-usb-files.html)
&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;
Are you sure that the grafic card is broken? Have you tried to reset the nvram (cmd+opt+P+R)at boot up?
What do you get, when you press cmd+opt+O+F?

---

### Post by kudzugarden on 2008-12-03
> **tiresia said:**
> 
Are you sure that the grafic card is broken? Have you tried to reset the nvram (cmd+opt+P+R)at boot up?
What do you get, when you press cmd+opt+O+F?

nope, it isn't actually, that fixed it. thanks!!

---

### Post by tiresia on 2008-12-03
Good! Can you please mark your thread as solved?

---

