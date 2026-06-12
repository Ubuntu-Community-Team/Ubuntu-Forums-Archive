---
title: "[SOLVED] X has gone"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by flyby42 on 2008-04-19
I am running Gutsy and have been doing so for a month or so.  I was playing around with Xine.  I had a few issues and while trying to resolve these I ended up using Synaptic to uninstall Xine.  Part way through X closed with errors and I left it for 20 minutes or so expecting X to restart.  It didn't.  Now when I restart Ubuntu X fails to start.  I was thinking or reinstalling Xine but don't know the commands to do this without Synaptic.  Any help gratefully recieved.

Steve

---

### Post by TeoBigusGeekus on 2008-04-19
Type 

```
startx
```

to try to start x (:))...


If that is no go, type

```
sudo dpkg-reconfigure xserver-xorg
```

to do some readjustments to your graphics.

---

### Post by Unitux on 2008-04-19
try this one
```
sudo apt-get install xine-ui
```

---

### Post by flyby42 on 2008-04-19
> **TeoBigusGeekus said:**
> Type 

```
startx
```

to try to start x (:))...


If that is no go, type

```
sudo dpkg-reconfigure xserver-xorg
```

to do some readjustments to your graphics.

startx got x started again.  However on restart x once again fails to start automatically and I need to login in the tty session restart x manually.  Must have broken something  Any idea what.

Steve

---

### Post by TeoBigusGeekus on 2008-04-19
I don't know what you have broken, but do run

```
sudo dpkg-reconfigure xserver-xorg
```

from a terminal and do all the adjustments for your graphics again...

---

### Post by flyby42 on 2008-04-19
I have run sudo dpkg....  It did clear up the issue I was having with Xine!  So thaks for that.  It appears that as Ubuntu starts it can not find some sort of init file so it can not start X.

---

### Post by erginemr on 2008-04-19
Now that your desktop is back, and if you would like to let Xine handle your video, you may consider installing Totem-Xine (Totem with Xine backend) and GXine:
```
sudo aptitude install totem-xine
sudo aptitude install gxine
```

---

### Post by flyby42 on 2008-04-20
I have found the solution to my issue.  

First a few more symptoms and better description.
From GRUB Ubuntu logo and progress bar would appear.  Near the end of the progress bar the logo would disappear and the splash screen would not appear.  Instead three lines would appear starting with Kinit:.  The last being Kinit: no resume image, doing normal boot...  The logon screen would not reappear but I would get a logon prompt as though in recovery mode.  The Kinit lines apparently are usual as the pc was not coming out of a hibernate.  I could login and start x using startx command.  Thanks to those that told me this as it greatly simplified things.  Once x started there were a few things I noticed.  
1) There was no shutdown option when shutting down.  Needed to log out of x then do a manual shut down.  
2) Update Manager was missing. 
3) Firefox went to a Google page with the firefox logo rather than the Ubuntu welcome file. 

What I appear to have done while trying to fix Xine was remove part of the Ubuntu desktop.  

To fix I shut the desktop down and ran

sudo apt-get install ubuntu-desktop

I found this information in another post and it fixed my problem.

---

