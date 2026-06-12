---
title: "New MacBook Pro with Penryn WIFI drivers"
date: 2008-03-15
forum: Apple Intel Users
---

### Post by DrAma999 on 2008-03-15
Hi,
these MBP have the Broadcom BCM4328 rev 5, i used the driver on the restore dvd for win with ndiswrapper but it doesn't work, i can see all the AP near me, but i can't connect on my airport extreme base station with WAP2 personal password and without protection.
Can somebody help me?
THX,
Andrea
PS:I'm using ubuntu 64bit

---

### Post by cyberdork33 on 2008-03-16
> **DrAma999 said:**
> Hi,
these MBP have the Broadcom BCM4328 rev 5, i used the driver on the restore dvd for win with ndiswrapper but it doesn't work, i can see all the AP near me, but i can't connect on my airport extreme base station with WAP2 personal password and without protection.
Can somebody help me?
THX,
Andrea
PS:I'm using ubuntu 64bitSounds like you are doing it right... you will have to post additional details about what you have done... Is there even 64bit capability in those drivers? Is ndiswrapper loaded? If you can see APs, then my guess is that the hardware is working, but "i can't connect" doesn't say much...

---

### Post by DrAma999 on 2008-03-16
Thank for the answer...
Yes the bcmwl5.inf file inside says that the driver is also for 64 bit, ndiswrapper is loaded, i had edit the modules file putting at the end of the page ndiswrapper.
The network manage shows me APs, i click on mine then i put the password...after that, comes the two points with the circle moving icon instead of the two monitors, it stays like that for about 3 minutes and then comes back the 2 monitors with the esclamation point.:(
 My AP is an airport extreme basestation.
thanks,
Andrea

---

### Post by cyberdork33 on 2008-03-16
sounds like your Router is not assigning an IP or something. Did you try it with encryption completely turned off? I am thinking it is just having a hard time with that AP for some reason. Can you try with some other access Point and see if you get the same issue?

---

### Post by DrAma999 on 2008-03-16
With encryption turned off... it works :D, but i can't keep my wifi without encryption...

---

### Post by cyberdork33 on 2008-03-16
> **DrAma999 said:**
> With encryption turned off... it works :D, but i can't keep my wifi without encryption...

Try WPA only, not WPA2. That may be the issue.

---

### Post by DrAma999 on 2008-03-17
> **cyberdork33 said:**
> Try WPA only, not WPA2. That may be the issue.
Nothing change...:(
I'm trying also this tutorial biut nothing has changed.

---

### Post by mechengineer on 2008-03-24
I'm having the same issue with my new MBP.  It's not essential that I have wireless under Linux because I have a hard line at my desk, but it sure would be nice to tote around and show off this awesome dual-boot setup, haha.

---

### Post by amonsul on 2008-03-24
same issue here.....

---

