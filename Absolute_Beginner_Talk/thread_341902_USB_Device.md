---
title: "USB Device"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Dave-C on 2007-01-19
Hey Whats The Sudo Code For Unmounting A USB Device I'm Using 

sudo fdisk -l 
...
...
pmount \dev\sda1 USB

To Mount The USB

---

### Post by kebes on 2007-01-19
You use "mount" to mount devices and "umount" to unmount them. Similarly if you're using "pmount" to mount something you can use "[pumount]("http://huygens.ca.infn.it/cgi-bin/man/man2html?1+pumount")" to unmount it. So try:

pumount /dev/sda1

---

### Post by Dave-C on 2007-01-19
AAWWWW See i tryed umount thinkin that you replace the p with u thinking that u would mean "unmount" i didnt have the p at the start thanks :D on my way to becoming a sudo master Lol take care and thanks

---

