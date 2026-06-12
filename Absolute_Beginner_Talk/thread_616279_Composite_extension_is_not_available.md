---
title: "Composite extension is not available"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-18
What do i do if i get this error when i try to change from "none" to normal in my desktop visual effects?
what does it mean?

---

### Post by shuttleworthwannabe on 2007-11-18
There are few threads here that could give you some guidance (also if you google the error, one hit will be on these forums)

Any, what grahics card are you using? If ATI, like myself, then you will have to install

$ sudo apt-get install xserver-xgl

Reboot or just restart x by CTRL+ALT+BACKSPACE

then try visual effects to your linking.

Also have you got compiz CCCM (GUI) installed? If not then then in add/remove search compiz and install it there.

Good luck,

S

---

### Post by moxer on 2007-11-25
After doing this i got all effects working great (thx  for that) but i can no longer play warsow. It now displays a msg saying i don't have direct rendering and that i should install the proprietary drivers, which i already have.

Any hints, or do i need to uninstall this?

---

### Post by Lagos on 2007-11-26
Installing xgl is a work around for ati cards, but it breaks direct rendering. 
Try removing XGL, installing the latest ATI driver, and setting composite extensions to "1" in your xorg.conf file. Reboot and see if that works.

---

### Post by JoshuaRL on 2007-11-26
Sorry to be such a noob, but how do you do that?  I've got the ati driver downloaded, but can't find how to install.  And how do I remove XGL, the add/remove GUI?  And how do I set composite extensions to "1"?

---

### Post by shuttleworthwannabe on 2007-11-28
HI JoshualRL, sorry I have been away from my desk for the last couple of days; catching up now.
 
About direct rendering and games on Ubuntu--I am not an expert on this, but the previous poster suggestion may work.
 
To remove xserver-xgl so this:
 
$ sudo apt-get remove xserver-xgl
 
To install ATI prop drivers--that too I am not sure how to do this, but this "dummies" [guide ]("http://ubuntuforums.org/showthread.php?t=575843")may be helpful
 
To set composite extention to "1" u will need to editt the 
/etc/X11/xorg.conf file
 
do this:
 
$ sudo gedit /etc/X11/xorg.conf
find somewhere toward the end of the file in the text Composite extension "0" and chnage the value to "1" [I would make a copy of this xorf.conf as backup before making any chnages just so that you revert to previous setting when needed]
 
Best of luck!
 
S

---

### Post by JoshuaRL on 2007-12-23
Thanks but I think I've found the problem.  I have an ATI Mobility Radeon M7 (7500) and fglrx doesn't support it.  So I have to find another way.  But thanks though!

---

### Post by JoshuaRL on 2007-12-25
Found the problem.  Needed some special settings in xorg.conf.  Now it works fine.  Still a little bit of work to do, but up from 200-300fps to 1140fps.  Sweet!

---

