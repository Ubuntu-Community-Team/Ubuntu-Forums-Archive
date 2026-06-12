---
title: "xorg.conf  Major Help needed"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by rasputin1575 on 2007-01-15
hello guys,
need some major help.
i've fiddled about with my /etc/X11/xorg.conf file and my laptop gone all bonkers.

Basically when i restart now, i **Do Not **get the usual ubuntu 6.10 interface but just a black screen with login and password required.

can someone help pls?

Am this close to just install ubuntu again, but i have so many things on this system already and this should be my last resort.

---

### Post by Jaydos on 2007-01-15
Hrm - I'm just new to Ubuntu/Linux, but that sounds like Login WIndow (System -> Preferences -> Login Window).
Ensure you have Themed as the style.

---

### Post by rasputin1575 on 2007-01-15
No man, as i said i dont get to see any interface. i lost it.. once i reboot i get a ms-dos-like screen where to log in and thats it.. it works like msdos , and i dont have any ubuntu's normal interface.

---

### Post by Jaydos on 2007-01-15
Hrm, soz for mis-understanding. Not sure what it could be if not that :S.

---

### Post by aidanr on 2007-01-15
ok, assuming you edited xorg.conf in text editor (gedit), you can log in from the command line and then type
```
sudo mv /etc/X11/xorg.conf~ /ect/X11/xorg.conf
```
what that will do is copy the automatically created backup from the last time you saved, over the newer xorg.conf

if that doesn't work, you can use 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by rasputin1575 on 2007-01-15
sorry mate, i used vi editor, silly me, so i dont have a backup.

---

### Post by teaker1s on 2007-01-15
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

---

### Post by rasputin1575 on 2007-01-15
tried that, but i dont know half the stuff there.. would it be possible for anyone to paste the contents of their xorg.conf file here, so that i can edit mine plsplspls?

---

### Post by rasputin1575 on 2007-01-15
forgot to mention, mine is a compaq presario 700 laptop..

---

### Post by teaker1s on 2007-01-15
well you need to find out the hardware you have like graphics chip etc then select the right options

---

### Post by rasputin1575 on 2007-01-16
Just to say thx to all the ppl tyring to help out on this matter.
Its sorted now.
I used the live CD to get back the xorg.conf file and then copied the contents on the corrupted one i fiddled with.
Regards.

---

