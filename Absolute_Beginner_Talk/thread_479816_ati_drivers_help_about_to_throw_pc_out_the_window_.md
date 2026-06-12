---
title: "ati drivers help about to throw pc out the window :("
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by kdiggdy on 2007-06-20
I've been working on this for the last 4 hours and i still cant figure it out
First 
I have a ati x700 gfx card
I have ubuntu fiesty x86_84

First when i put my gfx card in and load up ubuntu it does not load. It loads kernel and dies i cant read the msg it says it happens to quick. 
Second I put my gfx card in and load up live CD same thing.

Third I took out the gfx card and loaded up ubuntu
followed this guide
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
DID not work
I follwed a wiki on the ati drivers i found on the forums
DID the samething
What would happen is if i put the card in and load it up samething hapens as i sated above,
If i loaded it up normally without the gfx card it says I have a problem with xorg.conf
So i reset the original conf and i'm back to step 1

How do i install the driver lol

---

### Post by kdiggdy on 2007-06-20
8BUMP8 please anyone help!!!

---

### Post by 67GTA on 2007-06-20
Xorg doesn't yet configure on the fly. If you installed Ubuntu without the graphics card in, then it will try to load those settings. If it was installed with the card, then it will load those settings.You can't switch back and forth like that. You will have to put the card in, boot into recovery mode, and run "sudo dpkg-reconfigure xserver-xorg" That will take you through reconfiguring your xorg.conf file. If you try to boot again without the card then you will have the same problem. You might be able to have dual xorg files(not sure) and tell it which one to boot with. Maybe someone else canhelp with that.

---

### Post by drivel on 2007-06-20
The default ATI driver with Ubuntu is OK,at least you can open Desktop Effert & Beryl

---

