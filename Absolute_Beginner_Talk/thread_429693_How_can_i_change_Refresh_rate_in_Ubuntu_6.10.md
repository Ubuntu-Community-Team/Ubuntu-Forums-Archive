---
title: "How can i change Refresh rate in Ubuntu 6.10"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by zico87 on 2007-05-01
I am using ubuntu 6.10. I have a dual boot with Windows Xp. My graphics driver is Intel 845G (Integrated) and in Ubuntu it is i810 with supporting 1024x768, 800x600, 640x480. But all this resulation have 85Hz refresh rate. But my Monitor (Samsung sync master 792df) suports full screen view at 60 Hz. So it is not giving full screen view at 85Hz. so i need to change the refresh rate. How can i do that. Please help me:( :confused:

---

### Post by NT4usB on 2007-05-01
you can reconfigure X using the command```
sudo dpkg-reconfigure xserver-xorg
```
I would suggest backing up xorg.conf in case you bork it```
sudo cp /etc/X11/xorg.conf /etc/X11/bkup.xorg.conf
```reverse to restore.

---

### Post by Sef on 2007-05-01
Check System > Preferences > Screen Resolution.   You should be able to set your refresh rate to 60 from there.

---

### Post by starcraft.man on 2007-05-01
I have a question relating to this. Its been a slight problem for a while, I got a VP930b, nice screen but after putting in beryl, my screen seems to have changed the refresh rate without my input. It defaulted to 50 hz instead of my preferred 60-70. I don't really wanna do reconfigure xserver, nor do I get either preferred rate in the drop down menu. Is there a simple line of code I can insert manually into the xorg.conf to get it to 60hz ?

Edit: Just a note, but in the beryl general options it does say my refresh rate is set to 60? Kinda confusing...

---

### Post by NT4usB on 2007-05-01
If you search around a bit, you'll see threads about folks having trouble with refresh and tweaking xorg didn't fix it but configuring xserver-xorg did.
ymmv...

---

### Post by tophatandy on 2007-05-01
are you now allowed to steal threads?

but anyway..
to answer the thread theif's question..

reconfigure xserver-xorg its not that hard to do.. 

```
sudo dpkg-reconfigure xserver-xorg
``` 
from the cli accessed from the GRUB menu.

This will solve it..

---

### Post by NT4usB on 2007-05-01
> **tophatandy said:**
> are you now allowed to steal threads...

No more (or less) allowable than spanking someone for posting an on topic but slightly different question to a thread.
And, if anyone should be allowed to get pushed out of their bush by someone posting to their thread, it would be the OP.

---

