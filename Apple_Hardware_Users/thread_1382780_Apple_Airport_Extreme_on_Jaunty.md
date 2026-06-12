---
title: "Apple Airport Extreme on Jaunty"
date: 2010-01-16
forum: Apple Hardware Users
---

### Post by try2hard on 2010-01-16
Hello all. I am a new Ubuntu user and just installed Jaunty (9.04, I think) on my iBook G4. Everything was surprisingly smooth with the installation and setup. Ubuntu recognizes my wireless card (it shows a signal indicator in the top menu bar). However, I can't get it to connect to my network. My wireless is open and I entered my static IP and DNS servers.

I have read various problems between Ubuntu and Apple's Airport Extreme card.

Please let me know if anybody has a work around.

Thanks,

Nick

---

### Post by linuxopjemac on 2010-01-16
you can try if wicd works better than gnome's networkmanager:

```
sudo apt-get install wicd
```

this will automatically suppress networkmanager.

---

### Post by llamabr on 2010-01-16
Have you tried it with any other network besides your own?  That is, maybe it's a wep/wpa problem?

I run debian lenny, not ubuntu, on my ibook, but I've never had any trouble with the airport card.

---

### Post by try2hard on 2010-01-16
I haven't tried it with another wireless network. I did try it with an ethernet cable today and it connected and I could ping my router, etc. but still couldn't get a web page to load in Firefox.

I know this is a Ubuntu forum but, how do you like Debian Lenny on your Mac? Is it available for PowerPC? I really like Ubuntu because being somewhat of a Linux newbie, it seems pretty easy to use. I just need to get the Airport card figured out and I'll be all set.

---

### Post by llamabr on 2010-01-17
If it didn't work even with the cable plugged in, then it's a problem with your router, not with your wireless card, or even your instalation.

with that said. ubuntu no longer formally supports the ppc architecture.  There are still people updating packages and things, but it's only going to worse.

Debian does still maintain the ppc architecture, which is why most ibook folks are running lenny, instead.

---

