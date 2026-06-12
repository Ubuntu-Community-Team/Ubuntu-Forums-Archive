---
title: "ubuntu not stating properly"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by halfhearted on 2008-02-04
I just installed ubuntu 7.10 on an oldish Dell Latitude from a cover disk. It seemed to work fine. ubuntu started OK and asked me to upgrade. I upgraded and it downloaded 186 files and installed them. It took hours. When I restarted I foolishly went to change desktop background. Then even more foolishly I selected the Visual Effects tab and changed from 'None' to 'Normal'. Ubuntu asked me if I'd like to download and install an accelerated Nvidia graphics driver. Like a true mug I said 'yes'. Ubuntu will not now start. Clearly that driver was a mistake. I get a couple of drum beats and the screen goes black. I cant change anything because I can't see anything. Is there a way to see the desktop? Is there then a way to roll back to the previous driver which seemed to work fine in this old PC. Thanks for any suggestions.

---

### Post by jan quark on 2008-02-04
if you get to the login screen

try changing the session to gnome failsafe

it's a start

---

### Post by halfhearted on 2008-02-04
I do not. So, sadly, it isn't even a start. But thanks anyway. Any other ideas out there?

---

### Post by halfhearted on 2008-02-04
It seems that I have to run the live CD of Ubuntu and then open a terminal (how). From the terminal I will be able to change settings and maybe get back to the old graphics driver (how). So there's 2 things there I don't know how to do. Any help?

---

### Post by jan quark on 2008-02-04
just a guess

but when you load you see the grub loader, don't you?

try pressing escape, there is like few seconds when you can do this, and try booting into recovery mode

this should boot into a terminal mode

try to reconfigure your settings with this

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
```

startx
```

---

