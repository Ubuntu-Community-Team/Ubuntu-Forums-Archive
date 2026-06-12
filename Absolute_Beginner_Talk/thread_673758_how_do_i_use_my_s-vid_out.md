---
title: "how do i use my s-vid out"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Kedster on 2008-01-21
id like to put my mmovies through svid but when i do my laptop monitor shuts off andthe one on the tv iisent the right resolution and it all wide (i have a wide sreen laptop) what i am asking is if theres a way to sat the svid out up on a certian resolution and to keep the main monitor running like eather duplicate or expand both work if its easy

---

### Post by Kedster on 2008-01-21
bump

---

### Post by Golem XIV on 2008-01-21
You can play around with the "Screens and Graphics" menu option under System->Admnistration.

before you screw something up, however, you may want to make a copy of the working configuration file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

so if something goes wrong (as in not booting to a desktop) you can log into text mode and remove the screwed-up configuration:

```
sudo rm /etc/X11/xorg.conf
```

and restore the old (working) one:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Trust me, I've learned this the hard way. :-)

---

### Post by Kedster on 2008-01-25
ok i want to be able to extend it and use it another screen not a mirror of the defalt and it also says its diabed

---

