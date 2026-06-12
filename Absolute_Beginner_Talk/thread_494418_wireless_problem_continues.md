---
title: "wireless problem continues"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by jbrockk13 on 2007-07-06
I'm sorry to re-post this topic but I'm going crazy!!! I have a Compaq Presario v5000 laptop  with a broadcom built in wireless card. My wireless router is a D-link wbr-2310 hooked up to a computer running Windows xp. I've lost my original post but someone pointed me to a howto to get my wireless card to work but I've had no luck at it. In fact after I did all the steps Ubuntu doesnt even see the wireless connection. is there anything I need to do to start over. is any of my equipment incompatable? network manager doesnt even come up with a wireless choice now. please help me!!!](*,)

---

### Post by shearn89 on 2007-07-07
Hey - here are the howtos i used, and they seem to be really good (easy to follow, generally get it working alright):

1. Check [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") for info on your card.
2. If it says something about ndiswrapper, use [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") howto.

Post back if any trouble.

---

### Post by keval on 2007-07-07
Warning: I'm an utter newbie and just as likely to confuse as enlighten.
This having been said, I've just fixed a similar problem with my laptop (IBM Thinkpad running Feisty) by disabling the "wired" connection (System->Administration->Network->Network Settings).  It's possible my machine was looking for a wired connection and ignoring the wireless, or that it simply was confused by having two connections open simultaneously.  Dunno, but it seems to have worked.
Good luck,
Kevin

---

### Post by ntetreau on 2007-07-07
Once you gone through the howto mentioned above, take a look at the file /etc/network/interfaces.  As it happens to many people would try to get their wifi going, this file ends up being filled with lines describing eth0 and eth1, and others.  However, to use Network Manager, this file needs to describe only the "lo" interface.  So comment out all the lines which do not relate to "lo" by adding a # at the beginning of the line.

Nic

---

### Post by jbrockk13 on 2007-07-07
ok I got to step 2.5 step 7 about unzipping or using cabextract or unshield and I am lost! The file I downloaded is a .exe file and I cant open it or extract anything from it. I must be doing something really wrong cause I cant figure this out. Oh, and I still dont see my wireless connection in networking. HELP

---

### Post by shearn89 on 2007-07-08
You need to get the .INF and .sys files for the card, the .exe you downloaded is probably an auto-setup for windows. If you've still got the cd for the card, then you can copy them off that, otherwise hunt around the net for the files. Just type "your card name inf file" into google, and you should get something.

---

### Post by jbrockk13 on 2007-07-11
Thanks for the help guys but still not working. I think im going to have to a re-install and start over. I really wish the wireless would "just work" but it looks like it's going to be alot of work. whish me luck. Thanks

---

### Post by ugm6hr on 2007-07-11
How far did you get with this:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

It looks like it works for most people.  If it doesn't it is likely that it is a simple issue to resolve.

But before you do - it's worth confirming the following:
Are you using Feisty/Ubuntu7.04?
Output from *ifconfig* and *iwconfig*
It's definitely a BCM4318 (check with *lspci*)

---

