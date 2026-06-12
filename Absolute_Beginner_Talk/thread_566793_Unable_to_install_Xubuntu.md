---
title: "Unable to install Xubuntu"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by dndrich on 2007-10-03
Ubuntupals:

I have installed Ubuntu 7.04 on an old Gateway Pentium III with 256 meg memory.  It installed fine, but runs a bit slow.  So I decided to do a complete fresh install using Xubuntu, figuring it would run faster.  I have run the Live CD, and when I install, I fail at the partition point.  What happens is, I am trying to use the whole hard drive, and when it trys to partition, it fails.  The message is something like failed to partition sda 0.0.0.  When I look at the message, it says can't unmount, or something like that?


I tried multiple things, including unmounting the disc by right clicking on the icon and unmounting...no go.  Hard to understand, since I installed Ubuntu no problem on this computer.  This is not a duel boot.  Ubuntu is clean on this computer, and I want to erase it and install Xubuntu.  Thoughts?


Daniel

---

### Post by Clay_Banger on 2007-10-03
you could try using gparted to manually setup the partitions before installing, then during the install just point to each partition as '/', '/home' etc.. instead of letting the inbuilt partitioner do it for you.

---

### Post by dndrich on 2007-10-03
I think I tried something like that.  I started Gnome Partition Manager that is in the system menu on Xubuntu.  I tried to delete the partitions and reformat.  It just didn't seem to let me do it.  So I tried to run the partition manager by using terminal, and gksudo, but I could not get the terminal to run with the live CD.

---

### Post by Pumalite on 2007-10-03
Better try this:[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by dndrich on 2007-10-03
Hmm.  Do you mean I should try the alternate disk?  I installed Ubuntu with no problem using the standard live CD for i86.



Daniel

---

### Post by om1 on 2007-10-04
if you steal can boot to your install of ubuntu run this in terminal
```
sudo aptitude install xubuntu-desktop
```

---

### Post by dndrich on 2007-10-04
OK, but how does that help?  I want to clean install xubuntu.  If I install xubuntu desktop, how do I start it?

---

### Post by om1 on 2007-10-04
you can find more info here...
ps you can add or remove desktop environments at will
here is a place with some info on how to login to different desktop environments  
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)
ps you can remove the ubuntu install by this
```
sudo aptitude remove ubuntu-desktop
```

---

### Post by dndrich on 2007-10-07
OK, what I did was to go ahead and download the alternate CD, and install from it using the text method.  It worked perfectly, and now I have a clean install of xubuntu on that computer.  Don't know why the live CD didn't work, but there you go.

---

### Post by Chilongola on 2007-10-07
Your problem was your memory.  In text mode the burden was less.

---

