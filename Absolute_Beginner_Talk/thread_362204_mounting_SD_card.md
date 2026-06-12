---
title: "mounting SD card"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by macruadhi on 2007-02-15
I have had Ubuntu 6.06 installed for about 2 weeks now. When it was first installed it would recognize and mount my SD memory card (it even recognized it's name, Kodak) and now I've tried to get it to recognize it by booting with the card inserted, not inserted, and just simple log-off, log-on. Still nothing. 

Thanks
Eric

---

### Post by louis_nichols on 2007-02-15
There might be several reasons to this problem.

First, it might be that gnome-volume-manager doesn't start with your Gnome session. You can recognize this if CDs and DVDs are recognized automatically upon insertion. If they aren't, then you juust need to open a terminal and type

```
gnome-volume-manager
```
then press enter, and you should be alright. You might need a logout/login, but I don't think so

If the above doesn't work, the problem might be more complicated. In this case, you should try mounting the SD card manually and see if that works.

Of course, you need first of all to make sure that the SD card is alright, by checking if it works in other PCs.

---

