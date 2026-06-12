---
title: "How do I reset my video card in ubuntu"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Crazy tech on 2006-07-26
Hi I need help with the ubuntu install. I had an video card go bad and now I can't get the graphical desktop to run  with the onboard video ,It tells me to type in etc/xorg.config but when I do, It tells me no file or dir of this type. I'm a noob so please excuse my use of dos like commands.

---

### Post by aysiu on 2006-07-26
Try this: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can; otherwise, go with the default. ```
sudo /etc/init.d/gdm start
```

---

### Post by Crazy tech on 2006-07-26
Thanks I'll Give it a try.

---

### Post by Crazy tech on 2006-07-26
Got it working but the onboard video is very sluglish in games like ut2004.

---

