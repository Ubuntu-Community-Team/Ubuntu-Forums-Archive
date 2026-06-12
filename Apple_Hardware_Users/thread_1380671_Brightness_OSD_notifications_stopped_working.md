---
title: "Brightness OSD notifications stopped working"
date: 2010-01-13
forum: Apple Hardware Users
---

### Post by spockrock on 2010-01-13
Hi folks,

I am having a weird issue where my brightness keys on my macbook v4.1 work, but for some reason the brightness notifications have stopped working.  I can clearly press the buttons to reduce and increase the brightness, but no notifications.  Network manger, sound, firefox, amarok notifications work, but not brightness.  It did popup, but I am note sure when or what update broke the notifications.

---

### Post by mario_k8 on 2010-01-16
Hello. 

I don't have an answer, but I'd like to add that the same thing happened on my Compaq Mini 110c so this might not be a strictly Apple-related issue. Brightness function keys still work for me as well but OSD indication is no longer visible. My only guess is that some of the recent updates broke this, but can't tell which one for sure. 

Anyway, if anyone finds out something about this, please let us know.. 

Cheers!

---

### Post by hollowtd on 2010-01-16
I had the same thing on my macbook 1.1 too with Karmic.

---

### Post by linuxopjemac on 2010-01-16
I have it too on my MacBook 2,1

---

### Post by linuxopjemac on 2010-01-17
[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/508713](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/508713)

---

### Post by linuxopjemac on 2010-01-19
If you want this bug to disappear, you have to also add your name to that bug, if more users report it, it might get fixed....

---

### Post by mario_k8 on 2010-01-24
That's weird. The OSD notifications went all back to normal today! I can't remember for sure if I downloaded any new updates in the mean time. Oh well, I'm back to super-happy mode with ubuntu on my netbook! Hope the same happened to the rest of you :D

---

### Post by linuxopjemac on 2010-01-24
For me it still doesn't work...not that I care so much about it though.

---

### Post by mario_k8 on 2010-01-26
I think i spoke to fast, but I did notice this:

Brightness OSD notification disappears only when my netbook is running on battery.
If I plug it in and reboot, the notifications go back to normal.

Is it the same for anyone else?

---

### Post by linuxopjemac on 2010-01-26
not for me

---

### Post by spockrock on 2010-01-30
nope still doesnt work yet for me.

---

### Post by gbm31 on 2010-05-28
ok, here's another patient.

the brightness notification stopped working, all other notifications work.

asus eee 901, ubuntu netbook edition 10.04, eee-control 0.9.6.2.

I don't think it's funny that they closed the bug saying that some laptop models do adjust brightness in hardware without sending notification events to the os.

that's simply bullshit because it worked for a while...

---

### Post by gbm31 on 2010-06-02
Update:

It's working again!

Guess what: I reinstalled indicator-messages (yes, that envelope thing, because I wanted notifications for my dates, since I started using the pimlico suite) and after logout/login the brightness notification is there again.

You guys deinstalled that, too?

---

