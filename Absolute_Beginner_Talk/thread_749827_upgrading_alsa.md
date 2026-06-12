---
title: "upgrading alsa"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-04-08
i tried to do a ./configure, make, sudo make install and restart but ubuntu is still using 2.0.15 and not 2.0.16.  it there something else i need to do.

---

### Post by stmiller on 2008-04-08
There are instructions here on how to upgrade alsa:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by neurostu on 2008-04-08
when you say ubuntu is using 2.0.15 not 2.0.16 what are you refering to?

---

### Post by RyanZec on 2008-04-09
> **neurostu said:**
> when you say ubuntu is using 2.0.15 not 2.0.16 what are you refering to?

I mean the the 2.0.15 alsa driver is installed by default and when i install the 2.0.16 driver ubuntu is still using the 2.0.15 driver.

---

### Post by kpkeerthi on 2008-04-09
The latest alsa version is 1.0.16. 

Ubuntu does not continuously update to latest versions of packages available upstream unless there are critical security fixes. You need to wait for 6 months until a new Ubuntu version is released. That being said, you can use the backports repository from System -> Software Sources and hope for some one to backport the latest version of your favorite packages for gutsy. The other option is to compile from source.

You can find instructions to compile alsa from source [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

