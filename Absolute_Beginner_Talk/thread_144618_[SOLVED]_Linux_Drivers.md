---
title: "[SOLVED] Linux Drivers"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by Xander {MP} on 2006-03-14
Sup Everybody,

I hate to admit this but I am a newbie to Linux! I need help finding drivers for a wireless nic? Where can I get them?


Thx,

Xander {MP}

---

### Post by taurus on 2006-03-14
What brand and model is your wireless card?  You need to provide a little more info before anyone can assist you with it.

---

### Post by jjf on 2006-03-14
taurus,

I could be wrong about this, but my understanding is that if Ubuntu does not automatically detect your wireless NIC, then you will need to use a program called ndiswrapper (it allows you to use the Win XP driver in Linux).  Detailed help can be found here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

You will need to know the model of your wireless NIC.

---

### Post by landotter on 2006-03-14
check to see if it got automatically configured, a lot do. It might be called eth0 or ath0

if not, search the forums for ndis wrapper

---

### Post by dicecca112 on 2006-03-14
[QUOTE=jjf]taurus,

I could be wrong about this, but my understanding is that if Ubuntu does not automatically detect your wireless NIC, then you will need to use a program called ndiswrapper (it allows you to use the Win XP driver in Linux).  Detailed help can be found here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

You will need to know the model of your wireless NIC.[/QUOTE]


yup that's exactly right, be beware a lot of times getting them to work is damn near impossible, and when you do, its intermittent at best

---

### Post by taurus on 2006-03-14
[QUOTE=jjf]taurus,

I could be wrong about this, but my understanding is that if Ubuntu does not automatically detect your wireless NIC, then you will need to use a program called ndiswrapper (it allows you to use the Win XP driver in Linux).  Detailed help can be found here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

You will need to know the model of your wireless NIC.[/QUOTE]
Yes BUT if you can list your brand and model, perhaps somebody has figured it out and can give you a pointer.  Breezy didn't see my Linksys Wireless WPC54G in my laptop and I had to use ndiswrapper to install a driver from Linksys' site and everything is working great since but hey, it's up to you if you want to list it here or not...  I am not going to cry over it.

---

### Post by Xander {MP} on 2006-03-24
Thx for all the advice!!! Fortunately a customer support person from US Robotics got back to me and told me they have linux drivers for the card. Got it all installed now.


Thx Again,

Xander{MP}

---

