---
title: "Cannot Hibernate"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by taco_truck on 2007-01-15
When i click on hibernate, the cursor at the top left of my screen blinks for about 5 seconds, then it says "not enough free swap."  Whats the problem, and how can i fix it?

---

### Post by puneit on 2007-01-16
Post details of your system.
How much Swap is available?
What hardware you are using?

---

### Post by taco_truck on 2007-01-19
How do i get more "swap"?

I have a dell inspiron 6000 1G RAM, 1.7Ghz intel pentium m, ati x300 videocard 40GB HD.  6 for linux, 34 for windows..

---

### Post by puneit on 2007-01-20
Swap is usually created while installation. After installation you can create a swap-file, but its not working on my friend's toshiba tecra laptop.

---

### Post by JamieC on 2007-01-20
Can you please open a new terminal and post the output of "free".

---

### Post by mikewhatever on 2007-01-20
To check your swap type 'free' in the terminal.

---

### Post by casaschi on 2007-01-20
Had the same problem (lack of swap space for hibernating) and resolved by resining the swap partition using the gparted livecd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

After that it's likely that your swap file wont be mounted, so you need to do few things to get it mounted properly and used properly by suspend/hibernate, full instruction here:
[http://ubuntuforums.org/showthread.php?t=287962](http://ubuntuforums.org/showthread.php?t=287962)

---

