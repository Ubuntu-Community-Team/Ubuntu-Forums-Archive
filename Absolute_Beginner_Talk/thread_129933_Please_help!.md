---
title: "Please help!"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Mr X on 2006-02-15
HELP ME PLEASE! MY SCREEN RESOLUTION IS STUCK ON 640x480!! THERE ARE NO OTHER CHOICES! What should i do?

---

### Post by Mr X on 2006-02-15
Sorry! Flalse alarm. I rebooted and worked just fine. \\:D/

---

### Post by Perfect Storm on 2006-02-15
First you can try:

Find your monitor manual and open thte terminal

```
sudo gedit /etc/X11/xorg.conf
```

Under **Section "Monitor"** change **HorizSync** and **VertRefresh** so it fit what it says in the manual.

reboot.

If that doesn't help try this:

```
sudo dpkg-reconfigure xserver-xorg
```

reboot.


More info: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Edit: ah ok, good to know ^^

---

### Post by Madpilot on 2006-02-15
[QUOTE=Mr X]Sorry! Flalse alarm. I rebooted and worked just fine. \\:D/[/QUOTE]

Sometimes if you start the computer without your monitor running, it resets to 640x400; restarting cures it.

It's done that to me a couple of times, now I'm careful to turn the monitor on when I start the box... :p

---

### Post by Mdups on 2006-02-15
[QUOTE=Madpilot]Sometimes if you start the computer without your monitor running, it resets to 640x400; restarting cures it.

It's done that to me a couple of times, now I'm careful to turn the monitor on when I start the box... :p[/QUOTE]

huh, Good to know! Thanks :)

---

### Post by anirban.sam on 2006-02-15
try,
sudo dpkg-reconfigure xserver-xorg

---

### Post by Mr.X on 2006-02-15
lol mr.x is my name :p

---

