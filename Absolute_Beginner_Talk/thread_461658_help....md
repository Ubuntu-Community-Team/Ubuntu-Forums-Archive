---
title: "help..."
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by dooze on 2007-06-01
my dad installed ubuntu (i don't know which version) on his computer after he was recommended by his colleague to do so.

i, myself, have never used ubuntu. so please bare with me for my shortcomings.

everything ran quite smoothly, until a couple of days ago. he told me the os loads as it should but when it goes into the login screen, it's blank with several white flashing lines. i dont think it's the monitor since everything before it is ok.

after loading and reloading the os several times i notice there was an error message:
buffer i/o error on device hda, logical block 39102336
hw_random: rng not detected

can anyone please tell me what this means?? is that the source of the problem. if so, how can i fix it??

regards,
firdaus

---

### Post by djheadley on 2007-06-01
It sounds like the hard drive is about to go bad, or maybe the data cable or power cable is not plugged in all the way.

device hda is a hard drive

---

### Post by dooze on 2007-06-01
ok thanks... i'll check it out

---

### Post by daimaru on 2007-06-01
when u get ur white lines or whatever does ur computer still respond can you actually still use it ? if you want more info hit ctrl+alt+F1   login using ur username and password (you ll be at terminal) type 
```
less /var/log/syslog 
```
to get more info on whats going on.

---

### Post by dooze on 2007-06-03
no... it's just a black screen with flickering white lines...

---

### Post by jonward0690 on 2007-06-03
Yea eather a cable is loose or the HDD is going bad.Might to try running a stress test on the hard drive.Here is a link to a free hard drive stress test. [http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

---

### Post by ncappel1 on 2007-06-03
If there's any inkling that the drive is about to go bad, then you need to back-up your data as soon as you can, you don't want to lose potentially important files/documents.

---

