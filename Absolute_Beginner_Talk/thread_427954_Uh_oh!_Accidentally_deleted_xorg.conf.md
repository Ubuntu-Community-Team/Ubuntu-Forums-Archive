---
title: "Uh oh! Accidentally deleted xorg.conf"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Dtree on 2007-04-29
I believe I have deleted my xorg.conf file, Hahaha fun fun fun
Ehh... now what

---

### Post by [S|G] on 2007-04-29
Try this:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bobplano on 2007-04-29
wow... i can't believe you managed to do that. i don't know how to recover it other than getting a copy somewhere. did you ever back it up? i don't think the command above will work because AFAIK it only reconfigures it, but you can still try it

---

### Post by Dtree on 2007-04-29
Hey, Thanks S.G. That worked
Have to resetup everything but thats life in the fast lane
And all this just to get my mouse working right~ can hardly wait to tackle Beryl

---

### Post by doomster on 2007-04-29
i did that 2 (delete xorg.conf) 2 days ago. i had to apt-get Lynx browswer , and search ubuntuforums.org  , in text based -console mode, for the "sudo dpkg-reconfigure xserver-xorg" solution :) lol
 quite an experience though , and i surely never forget the reconfiguration comand again:)

---

### Post by konungursvia on 2007-04-29
You should always back it up before doing anything to it.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

