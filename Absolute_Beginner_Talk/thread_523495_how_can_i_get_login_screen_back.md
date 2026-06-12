---
title: "how can i get login screen back ????"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Aamir Aziz on 2007-08-12
when i boot my computer after loading all, the login screen does not appear, only black screen appears with no cursor nor mouse pointer ...

  this is the 4rth time i'm facing this problem. before i used to install the fresh copy but this is difficult and time consuming for me..

   why it happens and what actually the problem is ???
   how can i solve it ???

---

### Post by SOULRiDER on 2007-08-12
Did it work before or it never did? I think what you should do is reconfigure xorg and see if that fixes it.
```
sudo dpkg-reconfigure xserver-xorg
```
I Suggets you backup your Xorg config, just in case by doing:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
```

---

