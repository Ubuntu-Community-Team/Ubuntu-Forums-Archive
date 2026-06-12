---
title: "cannot get it to work on a emac 1ghz"
date: 2006-11-03
forum: Apple PPC Users
---

### Post by tbluhp on 2006-11-03
I use a emac 1ghz and cannot get it to work affter it shows the ubuntu boot screen (ubuntu words and status bar with black background) my monitor seems to turn off and cannot do nothing more makeing me turn off my mac and reboot? Why cannot ubuntu work on my emac?

---

### Post by 3rdalbum on 2006-11-03
It can work:

drop to console by pressing ctrl - option F1
** this means once you boot up to a blank screen hit the 'ctrl' key, the 'option' key and the F1 key all at the same time. you'll be in a terminal window. **

** if you need to log in, use the name "ubuntu" to log in. **

and edit the X config file as follows:

** type this in exactly as you see it**
sudo nano /etc/X11/xorg.conf

change the frequencies in monitor section as follows:
** find this part in the file you are now in (xorg.conf) and make these changes **

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 60-60
VertRefresh 43-117
EndSection

** after you have made the changes, press Control-X, then the Y key, then Return. **

** restart X by typing: sudo /etc/init.d/gdm restart


Instructions modified from twongkee and stepore's instructions.

---

### Post by tbluhp on 2006-11-03
i tryed what you said and when it said starting gdm manger and said failed.

---

### Post by tbluhp on 2006-11-03
could someone help me??? :(

I have the live cd version

---

### Post by linear on 2006-11-05
Search on "eMac" in this forum, I believe there are some different settings that you will need in xorg.conf.

---

