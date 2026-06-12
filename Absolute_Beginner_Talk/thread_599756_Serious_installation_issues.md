---
title: "Serious installation issues"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by TalioGladius on 2007-11-01
So I decided to go to Ubuntu at home, which would then have me running it on all my machines.

Wouldn't boot to the cd. Bunch of failed to set xfer mode errors. Unplug all hard drives...boots like a champ. Figured out that it didn't like one of my drives....which coincidentally was the one I wanted to install the OS to.

No matter, move files around and boot to the cd without problems. Go to install and the thing hangs up. wtf. Bought a new hard drive because I needed one anyways and the ****** locks up at creating the partitions.

I've never had issues with it until now and it's really starting to annoy.

c2d 6420
4gb ram
geforce 8600GTS
abit ab9 pro

any ideas?  Windows boots and installs without problems.

---

### Post by twiceasworn on 2007-11-01
What speed did you burn disc, if you did in fact burn from an iso? It is not recommended to burn faster than 4x.  Also, have you checked the cd for errors?  If you can't get the live cd to work, try the alternate text based installer.

---

### Post by TalioGladius on 2007-11-01
> **twiceasworn said:**
> What speed did you burn disc, if you did in fact burn from an iso? It is not recommended to burn faster than 4x.  Also, have you checked the cd for errors?  If you can't get the live cd to work, try the alternate text based installer.iso and burned at maximum.

What kind of sucks is that I'm now out of cd-r's.  :-(


BTW

all sata drives and cd/dvd drive

---

### Post by TalioGladius on 2007-11-01
Hmm...booted to a feisty cd.  Didn't lock up but says failed to create partition...

---

### Post by jwo7777777 on 2007-11-01
Still thinking......

---

### Post by TalioGladius on 2007-11-01
> **jwo7777777 said:**
> Are the CD and target HD on the IDE channel?
If so, are the set as master/slave or master/master?  (set them up master/slave or you will have problems) It is typical to make the HD master and the CD slave.

It is way better to not have the HD on the same IDE channel as the CD, though.

HOpefully you have the HD on one of the SATA ports and the CD on something else.  This eliminates the IDE master/slave issue.

Still thinking......Both cd and hdd's are sata

---

### Post by jwo7777777 on 2007-11-01
Do you know whether or not you can partition the hard drive under other OSes (FreeDOS, WIndows, etc....)?

---

### Post by TalioGladius on 2007-11-01
> **jwo7777777 said:**
> Do you know whether or not you can partition the hard drive under other OSes (FreeDOS, WIndows, etc....)?Trying vista now...

---

### Post by TalioGladius on 2007-11-01
Partition creates, deletes, and recreates of different sizes without problems when booting to the vista disk.

---

### Post by TalioGladius on 2007-11-01
Strange.  I really don't want to go to another distro...

---

### Post by jwo7777777 on 2007-11-01
I'm seconding the CD image at this point OR an issue with the 965 chip driver.

According to the hardware wikis for ubuntu, the 965 should work, but one installer had hang issues with PATA. [https://wiki.ubuntu.com/Intel_DG965WHMKR](https://wiki.ubuntu.com/Intel_DG965WHMKR)

---

### Post by TalioGladius on 2007-11-01
Unreal.  I can't believe that's what it was.


:guitar:

---

### Post by jwo7777777 on 2007-11-01
What's the status, Talio?  I'm not sure I understood your exclamation.

---

### Post by TalioGladius on 2007-11-01
> **jwo7777777 said:**
> What's the status, Talio?  I'm not sure I understood your exclamation.Burned another copy of the cd at the slowest speed possible and it boots and installs without a hitch.

Last thing I would have guess considering I did try several different cd's with the same result.

---

### Post by jwo7777777 on 2007-11-02
Glad it got sorted out.  You may want to see if there is a firmware update for the CD/DVD burner that made the bad discs.  You may want to stick solely to discs recommended for the burner you have (see [http://www.cdfreaks.com/](http://www.cdfreaks.com/) or similar).

---

