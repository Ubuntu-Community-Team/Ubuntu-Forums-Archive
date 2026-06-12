---
title: "problem getting mouse buttons to work"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by bigtwin on 2007-10-30
i've studied all the threads relating to this i could find, it seems simple enough even to a total ubuntu beginner like myself: just edit the /etc/X11/xorg.conf file. trouble is, i can't seem to get at it.

i tried this 

NOTE: You must be root to edit the xorg.conf file so in a terminal you should enter:
%>su
Password:<enter your root password>
%>gedit /etc/X11/xorg.conf

got this kind of message back

(gedit:6039): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


found & tried this:

Code:

sudo -i

then type password

Code:

sudo gedit /etc/X11/xorg.conf

then paste this over your old settings


and got a blank document.


what am i doing wrong?  why aren't the Forward & Back buttons on a standard Intellimouse on by default?  why is it so hard? 


BTW using 7.10

---

### Post by stump138 on 2007-10-30
so when you open /etc/X11/xorg.conf with the following code :

sudo gedit /etc/X11/xorg.conf

the contents of the file are blank?

---

### Post by ShogunMaster06 on 2007-10-30
sudo gedit /etc/X11/xorg.conf 

This should work.

Can you navigate to the file in Nautilus?  Can you see the file if you cd /etc/X11?

---

### Post by JBAlaska on 2007-10-30
Hopefully your following a howto: in this forum. A word of caution: if you mess up xorg.conf, X will not start!, this is not a big deal if you back up xorg.conf before modifying it (this should be covered in the howto's )

---

### Post by LowSky on 2007-10-30
are you typing x11 or X11, You get different results with each
X11 is correct
copy paste this into terminal

```
sudo -i
```then type password

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by bigtwin on 2007-10-30
> **stump138 said:**
> so when you open /etc/X11/xorg.conf with the following code :

sudo gedit /etc/X11/xorg.conf

the contents of the file are blank?

when i did it this morning, yes.

i just did it now, file was as it should be, i edited it, mouse buttons now work.

i can't explain why this should be, but from another's view it must look like user error. maybe, but it's not like i haven't tried that before :confused:

anyway, thanks for the help. i'm a happy bunny.

---

