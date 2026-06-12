---
title: "x server problem"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by lnxlvr on 2006-05-16
[http://ubuntuforums.org/showthread.php?t=175751&highlight=lnxlvr](http://ubuntuforums.org/showthread.php?t=175751&highlight=lnxlvr)

I posted on the above thread regarding my x server problems,but I didn't get any response/replies.Hence I'm posting it here.

I'm having the same problem as koech is having.I'm trying to run unbuntu 5.10 as a live cd on Dell Inspiron E1505 with intel duo core processor (Video Card Intel® Graphics Media Accelerator 950). I'm getting an x server error. Here are the last few lines of the /var/log/Xorg.0.log

I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,

i810e,i815,i830M,845G, 852GM/855GM, 865G, 915G, E7221 (i915), 915GM,945G

Primary Device is: PCI 00:02:0
(WW)I810: No matching evice section for instance (BusID PCI:0:2:1) found
(EE) No devices detected

Fatal server error:
no screens found

Does it mean that ubuntu didn't find any drivers for my video card? How to fix this problem?

Thanks
Lnxlvr

---

### Post by Koech on 2006-05-16
I had a similar problem as you a few days ago. I got info that I needed to install sth like resolution915, but I didn't go that far, someone advised me to go for Ubuntu Dapper Beta 2 which I am happy to report not only works but is also what I am using right now!! Try it, you'll like it. Now i'm working on WiFi installation.:-D

---

### Post by lnxlvr on 2006-05-16
Thanks Koech for the fast reply.Infact I had mentioned your post and your name too and you end up helping me out.Let me download it and play with it.

Thanks
Lnxlvr

---

### Post by Koech on 2006-05-17
I got your reply. How is it going? Have you managed to download Dapper? If so, how is it going?

---

### Post by lnxlvr on 2006-05-18
The next stable release is on june,so I'm waiting for it.Once it's released I'll download it and test it.Will definitely leave the feedback.Are there any differences between the Beta and the stable release?

Lnxlvr

---

### Post by prflfoawhgu on 2006-05-19
sudo nano /etc/X11/xorg.conf
Find a line with i815 in quotes and change it to vesa. i815 is the name of the driver that doesn't  work. Then type startx

The new version of dapper freezes in the install. I had to install in server mode then go sudo apt-get install ubuntu-desktop. Then the default driver works, but still has bad resolution. Had to use that 915resolution tool.

---

### Post by draven on 2006-05-24
[QUOTE=lnxlvr]The next stable release is on june,so I'm waiting for it.Once it's released I'll download it and test it.Will definitely leave the feedback.Are there any differences between the Beta and the stable release?

Lnxlvr[/QUOTE]

If there wasn't they would just release it now as stable.

---

### Post by lnxlvr on 2006-06-01
I downloaded ubuntu 6.06 and burned a live cd.It works perfectly.Awesome.Sound/graphics etc runs fine.Great job guys.

Lnxlvr

---

