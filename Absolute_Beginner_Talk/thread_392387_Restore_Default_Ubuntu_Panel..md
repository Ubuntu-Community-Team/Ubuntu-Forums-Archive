---
title: "Restore Default Ubuntu Panel."
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Babbage on 2007-03-24
Hi, I've deleted the default panel at the top of the Ubuntu desktop, (even though I got a confirmation dialog.)  Is there any simple way to restore this?
Thanks.

---

### Post by invalid on 2007-03-24
If you still have the lower panel, you can right click it and choose new panel. I do believe, however, any settings you applied to the old one will be gone, and need to be redone.

---

### Post by bulldog on 2007-03-24
Or hit ALT-F2 and type gnome panel.

---

### Post by bulldog on 2007-03-24
Double post

---

### Post by Babbage on 2007-03-28
Thanks for your replies.  I've replaced the old panel with my DIY version.  It'll have to do until I reinstall using Feisty Fawn next month.:)  I love a fresh OS just hot out of the oven, can't beat the aroma!!

---

### Post by komputes on 2007-12-13
I have gutsy and this reset the default panels for me:

Alt+F2

from here you have a choice of which terminal you want to use, the default is **gnome-terminal** (which is a bash terminal) or you can also use **xterm** as well.

Once you have a terminal window open it is pretty simple to restore the default panels (as they were when you first installed Ubuntu). In the terminal window type:

```
sudo debconf gnome-panel
```

Reboot and enjoy the default panels!

:popcorn:

---

### Post by nikoPSK on 2007-12-13
> **komputes said:**
> I have gutsy and this reset the default panels for me:

Alt+F2

from here you have a choice of which terminal you want to use, the default is **gnome-terminal** (which is a bash terminal) or you can also use **xterm** as well.

Once you have a terminal window open it is pretty simple to restore the default panels (as they were when you first installed Ubuntu). In the terminal window type:

```
sudo debconf gnome-panel
```Reboot and enjoy the default panels!

:popcorn:

now I also know for next time I mess up my panels. Thanks.

---

### Post by herbacious on 2008-02-20
saved :-)

---

### Post by nikoPSK on 2008-02-21
Please mark this thread as "SOLVED" by going to the top of the page and hitting the thread tools dropdown menu. :)

---

### Post by acesabe on 2008-04-06
Seems in Gutsy that this no longer works - but the solution here does:

[http://lists.ethernal.org/oldarchives/cantlug-0610/msg00566.html](http://lists.ethernal.org/oldarchives/cantlug-0610/msg00566.html)
[B]
gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel[/B]

---

### Post by agibby5 on 2008-07-14
> **acesabe said:**
> Seems in Gutsy that this no longer works - but the solution here does:

[http://lists.ethernal.org/oldarchives/cantlug-0610/msg00566.html](http://lists.ethernal.org/oldarchives/cantlug-0610/msg00566.html)
[B]
gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel[/B]


This worked great for me, even through reboots.  Thanks!  I just reverted from awn.

---

