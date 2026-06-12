---
title: "killing 2 computers---help!"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by ballyhoo on 2006-10-12
i've done this on my pc and now on my laptop. ](*,) 

changing the /etc/x11/xorg.conf file leaves me only the terminal type of interface after reboot or alt+ctl+backspace.

what info you need to help me out of this?
running 2.6.15.7 i686 is what the screen says.

---

### Post by sumguy231 on 2006-10-12
If you're made a backup of your xorg.conf, restore it with
```
sudo cp /etc/X11/<backup filename> /etc/X11/xorg.conf
```
If not, use:
```
sudo dpkg-reconfigure xserver-xorg
``` 
More importantly, back it up and be careful. ;)

---

### Post by ballyhoo on 2006-10-12
thanks

also found this helpful step by step [http://users.bigpond.net.au/hermanzone/p7.html]("http://users.bigpond.net.au/hermanzone/p7.html")

one down another to go.

---

### Post by sumguy231 on 2006-10-12
Glad to hear it. I like that page you dug up, by the way.

---

