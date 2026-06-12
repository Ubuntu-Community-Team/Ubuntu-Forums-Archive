---
title: "raid from sata?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Mick8882003 on 2008-04-04
I have onboard sata (ii?), is it possible to set up a raid array with this? (want to secure my data...)

---

### Post by tamoneya on 2008-04-04
use mdadm to make a raid out of several HDD

---

### Post by PointyWombat on 2008-04-05
Mick, your question is odd.

I assume you mean that you have an onboard (fake)RAID controller on your motherboard, and you have some SATA drives you wish to build a RAID out of, not including your system disks. RAID has virtually nothing to do with security.

Perhaps check out this link: [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

---

### Post by Mick8882003 on 2008-04-05
hmm, its the sata cable, the new red ones, and when i say secure data i mean keep it safe from going missing.

if hardy comes up trumps with usb disks ill be happy...

---

### Post by stefangr1 on 2008-04-05
A raid has to do something with data security. Since all hdd's will eventually die, mirroring them strongly reduces the change of loosing data. If you have a raid 1 array consisting of two disks, your computer will still be able to boot even if one of the two is gone. Complete data loss is thus reduced to thinks like theft of your computer, fire, or dropping it out of your hands when walking the stairs.

You should't use the sata controller of your IO-board though, since this is very specific to the brand and type you are using. If it breaks, you might have to find an exact similar board to get your data back (which can be difficult if it is already out of production).

If you wan't more data security, I recommend you to set up a raid 1 array using the Ubuntu alternate install cd.

---

### Post by Mick8882003 on 2008-04-05
good point, i didnt think of that, i was more on the train of thought that if its on the hd its safe

---

### Post by Mick8882003 on 2008-04-05
tell me is there much advantage to having said data on another hd within the same pc?

---

### Post by stefangr1 on 2008-04-05
> **Mick8882003 said:**
> tell me is there much advantage to having said data on another hd within the same pc?

The whole idea behind raid is to combine multiple disks to an array with either higher security or (for risk seeking individuals) better performance. It is not useful if you have only one disk. If you build a raid 1 array, the same data is automatically stored on two disks. This means that total storage capacity is cut trough half, at the advantage of higher reliability. It is thus especially useful for people that demand high reliability, but for normal users not very cost effective if the need a lot of storage. Mirroring 2TB is obviously a lot more expensive then mirroring 100GB. If you have data that you REALLY can't afford to lose, mirroring is a good idea since it is actually a more efficient (weighting reliability against costs) solution at todays disk prices than dvd burning is.

---

