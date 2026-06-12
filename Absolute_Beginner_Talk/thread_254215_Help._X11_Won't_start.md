---
title: "Help. X11 Won't start"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by awseft on 2006-09-09
I'm pretty new to Linux but have used it before. I got my video card drivers and installed them fine. I added a line in xorg.conf and now when I boot it kicks me to terminal. I made a backup but I cannot rename the backup as the original to overwrite it. I also cannot copy the backup over it. :( 

Now I'm stuck w/o it working. My backup is good or if I can edit the files in the terminal I can fix this problem.

Help... please help.:confused:

---

### Post by powder on 2006-09-09
If I were you, this is what I would do.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_borked
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
startx
```

---

### Post by stanz on 2006-09-09
might:
*sudo dpkg-reconfigure -phigh xserver-xorg*
then:
[I]sudo dpkg reconfigure xserver-xorg
[/I]do the change/help?

---

### Post by awseft on 2006-09-09
I used the first post and it got me back in but I hadn't backup right before I changed it like I thought. So it was all screwed up. I've decided to start over and do things in a differant order. I'll prob have another question or two later but I've gotten through this one (kind of).

---

