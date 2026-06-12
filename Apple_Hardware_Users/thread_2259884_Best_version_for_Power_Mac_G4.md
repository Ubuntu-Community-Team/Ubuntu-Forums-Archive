---
title: "Best version for Power Mac G4?"
date: 2015-01-07
forum: Apple Hardware Users
---

### Post by Vt3c on 2015-01-07
Hello everyone. I'm looking to put Linux on my Power Mac G4. I'm running just good ol' ubuntu 12.04 on it, and it's horridly slow. My specs are:

Dual 1GHZ PowerPC G4 (1MB L3) 
2GB RAM
64MB ATI Radeon 9000 Pro (may be why it's so slow lol) 
2x80GB HDDs and 1x30GB HDD.

What OS do you think would be best for this mac? I'm tempted to put Lubuntu 14.04 on it, but I'm not entirely sure yet.

---

### Post by rican-linux on 2015-01-07
Those specs should be good on 12.04 with Unity 2D. Lubuntu is much lighter desktop which should give a better performance.. Also try Debian stable with LXDE. I am running that on my powerbook g4 1.67Ghz 2G of ram.

---

### Post by Vt3c on 2015-01-07
> **rican-linux said:**
> Those specs should be good on 12.04 with Unity 2D. Lubuntu is much lighter desktop which should give a better performance.. Also try Debian stable with LXDE. I am running that on my powerbook g4 1.67Ghz 2G of ram.
How do I enable unity 2D?

---

### Post by Vt3c on 2015-01-07
Also, another thing, it doesn't appear to recognize my graphics card.

---

### Post by rican-linux on 2015-01-07
On the login screen there should be an option to change your desktop. If I remember if you click on the ubuntu icon near the login prompt it should work. For the graphics card what do you get when run this in terminal 'lspci |grep VGA'

---

### Post by ajgreeny on 2015-01-07
I used to have the next higher version of that card, an ATI Radeon 9200 Pro, on an old desktop machine and it was almost impossible to run Unity on that which is when I started using Xubuntu.

I have never been more happy with a DE or OS; it is the best of the *ubuntu family in my opinion.

Try it; you may like it.

---

### Post by rican-linux on 2015-01-07
Xubuntu is a great distro.

---

### Post by Vt3c on 2015-01-07
I use Xubuntu 13.10 on my laptop with a GMA 4500MHD, but a super snappy core 2 duo. It runs like new. Can anyone link me to a version of Xubuntu that works for my mac?

---

### Post by rican-linux on 2015-01-07
Look [here]("https://wiki.ubuntu.com/PowerPCDownloads"). You will need to follow the mini instructions? There use to be an iso for 10.04 but it is no longer there.

---

### Post by este.el.paz on 2015-01-07
> **ajgreeny said:**
> I used to have the next higher version of that card, an ATI Radeon 9200 Pro, on an old desktop machine and it was almost impossible to run Unity on that which is when I started using Xubuntu.

I have never been more happy with a DE or OS; it is the best of the *ubuntu family in my opinion.

Try it; you may like it.

Just adding my .02 that, I'm w/ ajgreeny on the general suitability of Xubuntu for PPC machines . . . and 12.04 is fine . . . you might be able to get 14.04 running, but then Xubuntu is not supporting PPC in 14 . . . you could try Lu 14 and then add the XFCE4 DE . . . it's not exactly "Xubuntu" but sorta like it.  On my G4 iMac which is down for broken RAM issues I had no plan to move from Xubuntu 12.04 . . . .

e.e.p.

---

### Post by ajgreeny on 2015-01-08
The problem in April this year will be loss of support for Xubuntu 12.04 which had only 3 years support, not 5 years as Ubuntu has.

---

### Post by Vt3c on 2015-01-10
> **rican-linux said:**
> On the login screen there should be an option to change your desktop. If I remember if you click on the ubuntu icon near the login prompt it should work. For the graphics card what do you get when run this in terminal 'lspci |grep VGA'
Entered lspci |grep vga, and it returned me to ~$. Didn't run or anything. Weird.

Edit: When I do just lspci, it shows up in the list of items as "0000:000:10.0 VGA compatible Controller: Advanced Micro Devices, Inc [AMD/ATI] R V250 [Radeon 9000 Series] (rev 01)", but for some odd reason it appears in the system -> details -> graphics it doesn't appear, and the performance on this thing even in unity 2D is pretty darn slow.

---

### Post by Vt3c on 2015-04-15
Still no luck with the mac. It's been sitting around.

---

### Post by rican-linux on 2015-04-16
You want to consier upgrading that video card.

---

