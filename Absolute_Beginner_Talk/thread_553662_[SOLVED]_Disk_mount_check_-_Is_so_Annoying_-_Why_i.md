---
title: "[SOLVED] Disk mount check - Is so Annoying - Why is it needed?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-18
Each time this happens, I feel like writing about it here, then I forget...
So why is this needed?

You take your laptop, you are at the cafe, you wanna show the new work project, flip open lid, power up, (now I'm expecting I can get straight to work, ...nope, it's all black and a stupid message)

"Disk has been mounted 30 times without being checked,disk check forced"

Aaaargh..... and it takes ages (so bloody annoying)

(Oh by the way Hibernate and Suspend don't work for me, just crashes, hope it works in Gutsy)

Why is this disk check needed, can I disable it?

---

### Post by splintercellguy on 2007-09-18
Why the check? A good intention to make sure you don't encounter a filesystem issue when it's REALLY inconveinent; to disable: sudo tune2fs -c 0

---

### Post by reacocard on 2007-09-18
It's to avoid bad filesystem errors, but if you use a journaled filesystem like ext3 (ubuntu default), then it is safe to disable it under most circumstances. To do so, run
```
sudo tune2fs -c0 /dev/sdXY
```
replacing /dev/sdXY with the partition you want to disable it on. You can find out what that is by looking in your fstab:
```
cat /etc/fstab
```
find all lines with ext3 in them, and run the tune2fs command on the /dev path listed on the line above.

---

### Post by hyper_ch on 2007-09-18
every 30ieth mount it does it... that's not often... well, I hardly ever turn my computer off...

---

### Post by MozartlovesUbun2 on 2007-09-18
> **hyper_ch said:**
> every 30ieth mount it does it... that's not often... well, I hardly ever turn my computer off...

Well on a laptop with an ATi card which isn't letting me Suspen or Hibernate, I sometimes do 30 boots in a day!!!

so that can be very annoying :mad:

---

### Post by hyper_ch on 2007-09-18
30 boots a day? You're torturing your notebook ;)

I see that it is annoying under those circumstances.

---

### Post by MozartlovesUbun2 on 2007-11-06
HowTo: Change disk checking/fsck at boot frequency
Hi,

Nearly all Ubuntu users know, that every 30 boots their system performs what is know as an "fsck" to make sure your hard drive has no errors.

If you go through periods of frequent rebooting, these checks can become annoying.

To change how often these boot up checks occur, run this command in a terminal:
Code:

sudo tune2fs -c 50 /dev/hda1

The two things in bold can be modified.

First, the number "50", which chooses how often you want the check performed. 1 makes it scan at every boot, 0 stops scanning altogether, and all other numbers mean the scan will be performed every ** boots, 20 for 20, 30 for 30, 40 for 40 and so on.

Next, the "hda1" which you simply change to match the location of your hard drive, be it hda1,2,3 or even sda1,2,3.

Setting the scan to never happen isn't recommended, I'd say between 50-100 is safe.

- Matt

---

