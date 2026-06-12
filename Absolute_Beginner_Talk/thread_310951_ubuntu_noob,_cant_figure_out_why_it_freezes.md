---
title: "ubuntu noob, cant figure out why it freezes"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Joshzz42 on 2006-12-02
so here i am figuring i want to get in on the linux action, i am fairly computerliterate but have never really messed wiht linux. So i hear from a friend that ubuntu is the way to go, i download the CD the hash checker and the imagine burn program. I check the hash and its good. I burn the cd and verify and its all good.

But, when i boot form cd and choose the "install/startup now" option it spends a few seconds with the loading bar going back and forth across the screen, then it will start loading its progress normally. When it gets like 90 percent of the way through loading it frezzes and the graphics get sorta screwey. The same thing happens if i try to start it in safe graphics mode. 

Any suggestions? or geusses at whats wrong? video card? also i have  a SATA hard drive and i hear that some distros have trouble with SATA....is ubuntu just not gonna cut it?

if anyone can shed some light id appreciate it, thanks.

---

### Post by 3rdalbum on 2006-12-02
If you press Control-Alt-F1 at the point where the graphics get screwey, what happens? If you get to a command-line, type:

sudo nano /etc/X11/xorg.conf

And press Return when it asks for a password. Now, with the arrow keys, scroll down to where it says "Section "Device"". If you can, write down what it says from this point on, until the bit where it says "Section "ServerLayout"". Post this information here, and we'll probably be able to figure out where things have gone wrong.

---

### Post by Joshzz42 on 2006-12-02
thank you much i am trying that right now

---

### Post by Joshzz42 on 2006-12-02
no go it just cuz a glitchy green dotted line to appear with the rest of my glitchy screen, i noticed that someone had a similaar problem several pages back and it was suggested that they try the alternate cd i think i will try that and see what happens for now, any further sugesstions appreciated

---

