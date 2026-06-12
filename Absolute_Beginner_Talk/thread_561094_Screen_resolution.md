---
title: "Screen resolution"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Metaphor on 2007-09-27
Hi.

I was having a problem (from one moment to another can't choose 1024, only 640 and 800) with the resolution and when i edited the xorg.xonf i guess i did something wrong and now i can't start ubuntu. He only starts in command line mode like if it was DOS...

anyway i've tried the gedit /etc/X11/xorg.conf in that mode and he says the display can't be opened...so how do i edit the file now???

i'm desperate!

thx

---

### Post by overdrank on 2007-09-27
> **Metaphor said:**
> Hi.

I was having a problem (from one moment to another can't choose 1024, only 640 and 800) with the resolution and when i edited the xorg.xonf i guess i did something wrong and now i can't start ubuntu. He only starts in command line mode like if it was DOS...

anyway i've tried the gedit /etc/X11/xorg.conf in that mode and he says the display can't be opened...so how do i edit the file now???

i'm desperate!

thx

HI you can edit that file with 
```
sudo nano /etc/X11/xorg.conf
```
But it maybe easier to reconfigure your xorg
```
sudo dpkg-reconfigure xserver-xorg
```
Good luck!

---

### Post by Metaphor on 2007-09-27
Done! Working like a charm :)

thx a lot one more time this forum is great ;)

see you in a near future :P

---

