---
title: "Finding the WLAN on a Compaq Laptop"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by brn on 2007-04-20
I have a brand new Compaq Presario C500 laptop.  It came with Vista installed and has a built-in 802.11-b/g WLAN that works with Vista and my existing DSL modem/router.  (I'm using it now.)  Using the Dapper live CD I tried to activate the wireless but all it showed was "ETH0" which it declared "active".  It did not show "WLAN0" as I expected.  This computer has a WLAN indicator which remained dark.  Before I undertake repartioning the disk and installing Dapper, (and before the no-fault warranty return period expires) I would like to ensure that this computer will indeed be compatible.  As anyone on this forum knows, the documentation accompainying the computer is vapid enough to drive a coyote off a carcass.  Can anyone suggest a way to activate the WLAN from the live CD?  If I push ahead and install Dapper will I find it there?  Any/all help/advice is appreciated.

---

### Post by oilchangeguy on 2007-04-20
where did you see eth0? go to system, admin, networking. what's listed?

---

### Post by brn on 2007-04-20
> **oilchangeguy said:**
> where did you see eth0? go to system, admin, networking. what's listed?

Exactly there oilchangeguy.  The other network connecton listed is dialup which this computer evidently supprots (An  RJ-11 jack suggesting this but I haven't tried it.)  As I mentioned in my original post, the documentation that came with the computer is painfully inadequate.

---

### Post by jiminycricket on 2007-04-21
Dapper is old, in fact Debian Etch is newer.  So, you might have better luck with Feisty Fawn's live cd.

But regardless you might be able to use ndiswrapper, or ndisgtk: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/) .  Of course you should be able to do all this stuff with the livecd, no installing required beforehand.

If you can look at lspci, it should tell you what your wireless card is called.

---

