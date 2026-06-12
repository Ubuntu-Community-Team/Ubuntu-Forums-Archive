---
title: "Problem Installing XP in Virtual Box"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by civicsi99 on 2007-07-05
im still fairly new to ubuntu but ive been reading the forums and just digging in and trying to learn. i read alot about virtual box and running xp inside of it and decided to give it a try. well i installed it using automatix and it starts fine. i created a new virtual machine for XP in virtualbox. well this is about as far as i can get bc it keeps giving me this message :
FATAL: Could not read from the boot medium! System halted.

i put my xp cd into the drive and mounted it but it wont start or boot from the cd at all. any suggestions as to what im doing wrong? any help is greatly appreciated, thanks.

---

### Post by felicity on 2007-07-05
You say you mounted the CD drive, does that mean ubuntu doesn't automatically mount your CD drive? Or it's a second drive?

Check the Settings in virtualbox under the new machine you made, and adjust the CD/DVD-ROM settings to match whatever CD drive your using, also making sure the Mount box is checked.

---

### Post by civicsi99 on 2007-07-05
sorry i should have been more clear. i meant that i have the cd/dvd drive box checked and it points to the correct drive. ubuntu is automatically mounting the cd when i insert it into the drive. thanks for your help.

---

### Post by felicity on 2007-07-05
Hmm, how about under the General, Advanced tab in settings, is the boot order correct?

---

### Post by civicsi99 on 2007-07-05
well its late and its driving me nuts trying to figure out and im going to bed. thanks so much for your heilp. ill get on here tommorrow and see what else i can find out.

---

### Post by frodon on 2007-07-05
You will find a full guide here if it can help you :
[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

### Post by civicsi99 on 2007-07-06
i got it working. i used my nlite iso file and just mounted that and got it installed perfectly. thanks for the help!

---

