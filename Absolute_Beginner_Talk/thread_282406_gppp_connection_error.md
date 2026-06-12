---
title: "gppp connection error"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-10-22
When I try to use gppp for dialup I get error[log file] saying that no access to /etc/pap & no access to /etc/chap which leads to me not being able to make a connection.  How can I rectify this?

#2 unrelated, when I minimize windows or apps they don't show up in "Notification Area" , instead they disapear to the bottom right of my desktop[my taskbar is on top & extra bar on right] the only thing that's in notification area is update icon[topbar]  Is there a setting some place thats wonky or something?

---

### Post by Mark_in_Hollywood on 2006-10-22
If gppp=gnome = gppp, and I think it does, you must use:

sudo wvdial 

in a terminal/console, instead of Gnome-PPP. I know it should work. I've been after this problem for months. My Gnome-PPP will no longer hold the connection for more than 10 to 12 seconds, before saying "that's it for now,  giving up" blah blah blah

If sudo wvdial will get you online, you're golden, for now. If it won't repost here with your type of modem Mfg./Model/#, internal/external, your Gno me-PPP is a graphic front end for wvdial, anyway. Wvdial should be 1.50 or better, although it probably isn't a "deal killer"

You can search this forum for my user name and modem and find many "zero response" posts. It's not Ubuntu, the underlying pppd/wvdia/kernel are probably where the flaw is.

-30-

---

### Post by randiroo76073 on 2006-10-22
I can get in with wvdial, I tried this with gppp:

gnome-ppp

gnome-ppp is a graphical frontend to wvdial and can be installed by $ sudo apt-get install gnome-ppp. You will find it in the Applications menu and the configuration is probably straightforward.

If wvdial works but you have problems connecting with gnome-ppp, view the wvdial.conf you created earlier in the wvdialconf section above:

gksudo gedit /etc/wvdial.conf

open the wvdial.conf file that gnome-ppp creates (in a different location):

gksudo gedit $HOME/.wvdial.conf

and compare the settings. Change the settings in the gnome-ppp wvdial so they match the settings in the functioning /etc/wvdial.conf. Do not delete lines--if you need to remove a setting, simply delete the text to the right of the = sign, eg. "Init3 = ". Despite the warning at the bottom of the gnome-ppp wvdial.conf file, you can add lines if necessary, eg. "Stupid Mode = on". 

and it's still no go, in fact now gppp says it can't open modem, at least before it would recognize and initiate the modem.  I tried shutting modem off then restarting, still nothing, even rebooting.

PS: External modem - Trendnet TFM-560X .  Supposed to be Linux friendly ](*,)

PPS: Just got "Modem Monitor" from the add to panel box working, tho mouseover says: "not connected"  Something is really screwy with the whole wvdial app!

---

### Post by natehatewindows on 2007-10-23
just do this [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html) .....it worked for me good. :)

---

