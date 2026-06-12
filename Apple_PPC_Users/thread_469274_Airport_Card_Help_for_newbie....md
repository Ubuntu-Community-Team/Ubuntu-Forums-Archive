---
title: "Airport Card Help for newbie..."
date: 2007-06-09
forum: Apple PPC Users
---

### Post by mleague on 2007-06-09
Okay, I know this topic has been discussed ad nauseum, but I am getting so frustrated.  Please help!

Running Feisty Fawn 7.04 on my Powerbook, installed from Alternative CD.  OS works great, but not Airport card.  I tried bcm43xx work around for Airport Extreme - no luck.  Perhaps I messed something up?

lspci shows ethernet controller, but does not show Network controller

iwconfig shows 

eth 1
AccessPoint=None
Link Quality = 0/92

Have tried several tutorials, including manually setting essid, ap, etc.  Have tried editing /etc/network/interfaces

I'm lost.  Can someone take the time t walk me through it?

---

### Post by El_Quintron on 2007-06-12
Run a search on here or on google for ' wl_apsta.o '
This is the driver for the broadcom card you're using on an ibook, then use the fwcutter as the command.

From there you should be able to use you AE card. There are lots of detailed instructions about this.

---

### Post by El_Quintron on 2007-06-12
Here are the step by step intructions:

This will give you links by ubuntu version:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")


And this is the one for Feisty:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty")

It's really not that bad once you get it going, if you're anything like me, most of your errors are from coding syntax rather than from lack of knowledge, but thanks to this you can just cut and paste everything.

Good luck!

---

