---
title: "Need Help with Xwindows Please...."
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-18
Hi people,
I must have installed wrong ATI drivers. (got them from the ATI site).

X will not start ever since. So now I need to uninstall all drivers and get gdm and xwndows working.
I get to text based logon.

I run xconfigurator with no luck.

Any thoughts ?

---

### Post by yabbadabbadont on 2007-09-18
```
sudo dpkg-reconfigure -p high xserver-xorg
```
Hopefully, you will be able to get X to start after that.  Then you can work on getting the correct binary drivers installed.  You might see if the Restricted Drivers Manager will install the correct ones for your card.

---

### Post by ROUBOS on 2007-09-18
I looked into /var/log/Xorg.0.log file. found the following error:
incompatible kernel module detected - HW accelerated OpenGL will not work

is this of any help resolving the problem ???

---

### Post by yabbadabbadont on 2007-09-18
Yes, it sounds like you installed the wrong drivers...  :)

Run the command I suggested and see if it helps.

---

### Post by alienexplorers on 2007-09-18
try using the envy script to load your drivers.  First uninstall the drivers you have using envy, then let envy load your drivers.  a link to envy can be found in my sig.

---

### Post by ROUBOS on 2007-09-18
> **yabbadabbadont said:**
> ```
sudo dpkg-reconfigure -p high xserver-xorg
```
Hopefully, you will be able to get X to start after that.  Then you can work on getting the correct binary drivers installed.  You might see if the Restricted Drivers Manager will install the correct ones for your card.

tried it with no luck. (EE) no devices detected

---

### Post by yabbadabbadont on 2007-09-18
Run the command again, and try selecting the vesa driver.  It should work with any modern video card, even if it will be slow.

Edit: or you could try following alienexplorers' advice.  It doesn't work now, so it couldn't hurt to try it.  ;)

---

### Post by ROUBOS on 2007-09-18
OK thanks that worked.
Now I'm in but the windows I open up like firefox and terminal cannot be moved around. One opens over the other etc.

No I need to uninstall all video drivers and start clean.. HOW ?

---

### Post by yabbadabbadont on 2007-09-18
[http://ubuntuforums.org/showpost.php?p=3387176&postcount=5](http://ubuntuforums.org/showpost.php?p=3387176&postcount=5)

:D

---

### Post by ROUBOS on 2007-09-18
OK did it. Keep getting an error message wen entering gnome, regarding the keyboard settings being different in gnome from X
and the splash screen takes ages to disappear. The other thing is that every window that I open up starts right on the top left hand corner of the screen and cannot be moved around.

Also in /etc/X11/xorg.conf file even though driver is set to fglrx, I get MESA on fglrxinfo command

---

### Post by yabbadabbadont on 2007-09-18
As a last resort, you might try backing up your data and reinstalling.  :(

---

### Post by ROUBOS on 2007-09-18
yes might be the only option. looks like a major stuffup. there are no window borders etc. bad think is that I'm half way down a huge torrent :(

---

