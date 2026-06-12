---
title: "Unable to install because of screen resolution"
date: 2006-07-03
forum: Apple PPC Users
---

### Post by UB2281 on 2006-07-03
I am trying to install Ubuntu 6.06 on a 700 mhz G3 iBook (dubbed the IceBook).

The big problem is that the installer-window is larger than the screen, and the control panel to set the Screen Resolution does not let me choose anything else than 640x480. There is a page for the model that came after mine on the testing team webpages, and it seems like it manages to get the correct 1024x768 resolution. However, not on this one!

See this webpage for the specifications (in detail) of the computer I own:
[http://www.lowendmac.com/pb2/ibook800.html](http://www.lowendmac.com/pb2/ibook800.html)

I was hoping maybe someone could be of some help

---

### Post by Qrk on 2006-07-04
I've submitted a bug about this issue... it really does put a damper on things. (My bug was about a Nvidia Graphics card, so it was not the same but similar)

I have two suggestions, the first is to use this command:

```
sudo dpkg-reconfigure xserver-xorg
```

And select a driver (the second dialog screen) that works with you hardware. (Hint, if you don't know one, try "vesa")

The second is to use the "alternate" install cd that uses the old Ubuntu installation program. Don't worry, that one is still quite easy to use. 

[http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-powerpc.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-powerpc.iso)

---

### Post by alien11 on 2006-07-07
Same iBook model, same probleam.

I was able to use the first method suggested by Qrk:

0. press ctrl+alt+f1 to switch to the first text console

1. enter command: sudo bash

2. enter command: dpkg-reconfigure xserver-xorg

   * choose driver 'ati';
   * enter PCI:0:16:0 as the PCI bus identifier of the card
     (should work also if left blank; however this was the default
      that I was offered, and it was correct);
   * for all other questions, the default is good; 

3. enter command: killall /usr/bin/X

   (I was not able to restart gdm by /etc/init.d/gdm restart)

after a while you will be presented with the graphical login at 1024x768...

---

### Post by tanner9gt on 2006-07-08
Hey, i'm having the same problem, but i found that you can hold the 'alt' key and then click and drag the installation window around with the mouse to read the parts hidden by your limited resolution

---

