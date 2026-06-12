---
title: "Wireless keyboard and mouse"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by BirdZerk on 2007-02-15
Hello,
A friend bought me a Belkin wireless desktop 130 set for christmas.  For the fun of it I plugged it into my xubuntu 6.10 installation.  I couldn't believe it, on reboot the mouse actually worked without touching a thing.  The keyboard is another matter,  I read in one of the threads to try
```
sudo dpkg-reconfigure xserver-xorg
```
they recommended to leave the ps/2 keyboard hooked up along with the wireless during reconfiguring, isn't that going to be confusing during the reconfigure?

---

### Post by Dainn on 2007-02-15
Hi 
I also use a wireless keyboard and mouse.   I noticed when I first set mine up that mouse was noticed right away and the keyboard wasn't.  It didn't have anything do with how the computer was configured, it was just the keyboard seemed to have a harder time connecting with the receiver.  My receiver and keyboard both have a "reset" button on them.  After a couple "resets" on both, the keyboard works fine.  This maybe something to try, if you haven't already, before changing other things.

---

### Post by BirdZerk on 2007-02-15
Reseting the keyboard didn't work, I think I will reconfigure xserver-xorg this weekend.

---

