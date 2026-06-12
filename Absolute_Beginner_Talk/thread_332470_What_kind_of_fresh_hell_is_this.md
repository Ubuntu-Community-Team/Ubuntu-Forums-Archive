---
title: "What kind of fresh hell is this?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by nextse7en on 2007-01-06
Hi there, new user on my 4th day of trying to install a workable version of ubuntu edgy.

finally got the wifi card up, thank to those who helped
Current problem is as follows.

My laptop sports an nvidia geforce go 6150, with this understanding, I downloaded the nvidia package for non legacy cards, once installed and invoked in my x .conf file "driver=nvidia" my x server would not come up, I could hear system sounds, but had no visual (just a black screen).

After reverting to the backup xorg.conf I had handy, the system came up with the generic driver. I decided to do my reaserch.

THE NVIDIA 6150GO IS REALLY A FLIPPIN' GEFORCE 430m, and requires a legacy freakin' driver.


So, no problemo, I'll just apt-get the legacy driver, right? WRONG!

EVERY time I try to download the legacy package, its corrupted!!!! Not only when I use apt-get, but also when I try to download it in synaptics, AND when I tried searching for, and downloading the package from the web, ALL ARE CORRUPT.

ACK!

I'm about to trash this installation all toghether, and trash this laptop, and go buy a mac.

If anyone can help, it would really be apprieciated.


Thanks so much.
Patrick

---

### Post by 23meg on 2007-01-06
What do you mean with "corrupted"? What error are you getting when you install with apt / Synaptic?

---

### Post by nextse7en on 2007-01-06
md5 bad checksum

---

### Post by kvonb on 2007-01-06
It's either the computer or your network.

When you boot, select memory test (you might have to press ESC to get the menu).  Sounds like either bad RAM or a dodgy hard disk to me!

Go buy the mac if you have the money, save yourself lots of headaches :mrgreen:.

---

### Post by teaker1s on 2007-02-20
save you a little grief, firstly the standard "nv" driver works with the 6150 as I'm using it. Secondly the 6150 for open gl requires the beta nvidia driver-search the forums there are howto's.

---

### Post by Vivix729 on 2007-02-20
If you are having so much difficulty installing the video driver, I suggest you try Automatix2 to install them.

---

### Post by teaker1s on 2007-02-20
automatrix kills gui with 6150-I found this out

---

