---
title: "Boot Issues - Shell Only, No Graphical"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Qharos on 2008-02-02
I'm having issues with my bootup; every time I do, I come to a terminal interface rather than a graphical one. I've talked to a couple people in the #ubuntu channel to no avail. 

Here's the errors I've received (I unfortunately can't recall which commands brought which errors, and can find out if necessary... but here's a list):

xinit: Connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error
Fatal server error: no screens found


What I've tried:

startx   (I believe this yielded the "no screens" error)
sudo /etc/init.d/gdm start  (ended up with [ OK ] but didn't resolve anything)
sudo dpkg-reconfigure xserver-xorg  (Installation-like screens, went through them, nothing fixed. Tried all the other commands after doing this one, too)
sudo aptitude install xorg-driver-fglrx  (no 'net connection, so it couldn't retrieve them)


Running Ubuntu 8.04 at the advice of someone in #ubuntu; needed to fix my Bluetooth and apparently this was the best way.
Laptop: Dell Inspiron e1405
Onboard videocard: 945GM Intel

---

### Post by LaRoza on 2008-02-02
You are using Alpha software, and weird things happen when one does that.

Does 7.10 work? It looks like your graphics should work fine.

---

### Post by Rocket2DMn on 2008-02-02
You need to reconfigure X.  Login to that terminal with your username and password.  The following will ask you questions about your computer hardware, do your best to answer - default options work for most things.  When asked about video drivers, select "intel" since you have an onboard intel card.  When asked about resolutions, use TAB to move and SPACEBAR to select your monitor's max resolution and everything less.
```
sudo dpkg-reconfigure xserver-xorg
```
Then run
```
startx
```

---

### Post by Qharos on 2008-02-02
> **Rocket2DMn said:**
> You need to reconfigure X.  Login to that terminal with your username and password.  The following will ask you questions about your computer hardware, do your best to answer - default options work for most things.  When asked about video drivers, select "intel" since you have an onboard intel card.  When asked about resolutions, use TAB to move and SPACEBAR to select your monitor's max resolution and everything less.
```
sudo dpkg-reconfigure xserver-xorg
```
Then run
```
startx
```

I'll try that... hopefully better luck this time. >.>


And 7.10 did work fine. So did the 8.04, and I haven't had any troubles to this point, and not sure why it suddenly sprung up. I'll give these a whirl and be back in a bit, hopefully with good news... I've been having problems for the last two days on various things...

---

### Post by Qharos on 2008-02-02
> sudo dpkg-reconfigure xserver-xorg

Tried that and restarted. It's now asking me questions about my keyboard and my mouse. It doesn't ask anything about video drivers, screens or anything else regarding the graphical interface.

Help please!

---

### Post by Rocket2DMn on 2008-02-02
It will get to those questions at the end, you gotta muddle through the other stuff first.

---

### Post by Qharos on 2008-02-02
The last questions is, "Emulate three button mouse."

It returns:

> x-serverxorg postinst warning: overwriting possibility-customized configuration file; backup in/etc/x11/xorg.conf.200802190857

---

### Post by Qharos on 2008-02-02
Also, I am getting another error after typing the command X that reads:

```
 Using config file: "/etc/x11/xorg.conf"
VESA(0); no valid nodes
Screen(s) sounds, but none have usable configuration.
Fatal server error: no screens found.
```

---

### Post by Rocket2DMn on 2008-02-02
You selected "vesa" instead of "intel" during the quesions?  If so, you can edit the file manually to make it correct:
```
sudo nano /etc/X11/xorg.conf
```
scroll to where it says
```
"driver" "vesa"
``` and change "vesa" to "intel"

---

### Post by Qharos on 2008-02-02
Your help is very much appreciated. Unfortunately, in that file, there is no "driver" or "vesa" listed. This has caused so many problems that I'm just going to reinstall Ubuntu.

Thanks for your help again.

---

