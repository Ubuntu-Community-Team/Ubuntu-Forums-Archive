---
title: "gnome-mount not working for usb port"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Epaminondas on 2007-08-16
I changed the default permissions for one of my usb drives by entering "dmask=0000" in options>volume>mount options. At this point, the drive still worked perfectly, although this did not solve the problem I was having. (I was trying to configure Unison, but the program would not copy to my flash drive, even though the default was umask=077. Unison wanted (I believe) umask=055.) The current problem started when I erased "dmask=0000" and closed the options window at which point the usb port went down. My usb drive is fine and works in other computers. I have also plugged into the port several different usb drives, and ubuntu does not mount any of them.  
my question is, how did I disrupt gnome-mount, and how do I reset everything? 
(the Unison question is for another thread, but nevertheless I would welcome any ideas.)
thanks in advance

---

### Post by Epaminondas on 2007-08-16
Not certain why, but when I restarted ubuntu, the drive started working again. guess this post is closed . . . .

---

