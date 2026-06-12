---
title: "How to locate mate-session-manager?"
date: 2014-05-03
forum: Apple Hardware Users
---

### Post by este.el.paz on 2014-05-03
```
sudo apt-get install mate-session-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mate-session-manager

```

Anyone offer any thoughts on getting a mate desktop session installed alongside??  the Xubuntu 14.04 64 bit install I've got going on my '10 MBPro?  I opened synaptic and saw "mate-desktop" as an option, so I closed synaptic and ran that in Terminal . . . logged out and back in . . . no mate de as option in log in window.  Opened synaptic, saw it shows "mate-desktop" installed, clicked on "mate-background" . . . same thing.  Back in synaptic, added "libmatewnck" and "wallch" to the package install list . . . restarted the computer . . . no mate session.

Searched the forum and found the post on the above command for "mate-session-manager" . . . got the error "unable to locate."  looks like I've downloaded at least 80-100 MBs of mate data this am, but so far no session showing up in the drop down session menu . . . .  Did notice that reviving from suspend brought no applets in toolbar and logout button would not work and had to shut the computer down . . . would there be any conflict in adding MATE next to XFCE that would make for such problems?  Or, that's another issue, one common to the 14.04 system?

e.e.p.

---

### Post by este.el.paz on 2014-05-03
Yes, just wanted to add that in various flavors of LM & 'buntu I've had multiple desktop sessions installed on top of the base system . . . by way of the Terminal and/or by way of synaptic; wherein the package and all dependencies are installed, and a simple log out gets the log in manager to add the new session . . . which can then be logged into w/o restarting, etc--easy-peasy.  There isn't this "partial" "install" . . . where things are apparently "happening" but leading to nothing showing up . . . ?????  Can anybody provide some insight into the why of this?  

e.e.p.

[Edit:  OK, I found the mate web site and see that it is not part of the official ubuntu repository . . . yet . . . .  They provide some options on trying to install, I guess if anyone had any experience with it that would be cool . . . .  I'll probably try it out tomorrow . . . .]
[Edit2:  OK, got the MATE 1.8 desktop installed . . . looks fine, the thing that I'm most happy about is that it brings the GNOME "Floating Feet" screensaver back!!!  That is a very funny screensaver . . . .]

---

