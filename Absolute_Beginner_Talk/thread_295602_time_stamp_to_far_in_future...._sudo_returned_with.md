---
title: "time stamp to far in future.... sudo returned with error"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Foudre on 2006-11-08
foudre@foudre-laptop:~$ sudo apt-get install xorg-driver-aiglx
sudo: timestamp too far in the future: Nov  9 10:06:40 2006
foudre@foudre-laptop:~$ sudo apt-get update
sudo: timestamp too far in the future: Nov  9 10:06:40 2006




odd thing that happened, infact since i've installed edgy this is about all i get, and randomly today sudo is returning with error (i get a little window saying that)

umm i've had an install on dapper loose its admin rights, i hope by some freak of nature i didn't loose them twice, i can't even change the time to get clooser to the timestamp thingy.

umm any one else run into this?

---

### Post by linear on 2006-11-08
There are other messages about this in the forums. One possible fix is supposed to be:

**sudo -k**

(if that doesn't work, search further)

---

### Post by Foudre on 2006-11-08
foudre@foudre-laptop:~$ sudo -k
sudo: timestamp too far in the future: Nov  9 10:06:40 2006

---

### Post by taurus on 2006-11-08
Check your BIOS to make sure the time and date are set correctly!

---

### Post by linear on 2006-11-08
Ok, I seem to have left out details. See this link: [http://www.ubuntuforums.org/showpost.php?p=1145634&postcount=10](http://www.ubuntuforums.org/showpost.php?p=1145634&postcount=10)

(A later post in that thread suggests **sudo** -v instead.)

---

### Post by Foudre on 2006-11-08
two reboots later, it randomly works, hmm i had this pop up a few days ago too, i'm just curious about how many others may have ran into this, it seams to be random, and a reset fixable problem,

---

### Post by Anonii on 2006-11-08
> **Foudre said:**
> foudre@foudre-laptop:~$ sudo -k
sudo: timestamp too far in the future: Nov  9 10:06:40 2006

1) Using the Adjust Time & Zone from the upper right corner clock, adjust the clock either to Nov 9 10:06:40 2006 or even later than this hour/date.

2) Use the following command:
sudo -K

3)Use Adjust Date & Time to set the date/time back to the correct values.

**EDIT: lol ok**

---

### Post by taurus on 2006-11-08
If your machine is in the net, why not enable ntpd at boot...

---

### Post by Foudre on 2006-11-08
no my machine has the right date and time november 8th 11:30
the time stamp thing is weird, and ntpd? is that like a internet time sync thingy?

---

### Post by taurus on 2006-11-08
> **Foudre said:**
> 
the time stamp thing is weird, and ntpd? is that like a internet time sync thingy?
Yip.

---

