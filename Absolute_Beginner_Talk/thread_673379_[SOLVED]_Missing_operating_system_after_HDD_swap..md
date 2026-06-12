---
title: "[SOLVED] Missing operating system after HDD swap."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2008-01-20
I had to load winXP on my computer yesterday because my wife's computer died. I disconnected the hard drive that contains the Ubuntu OS and connected a seperate hard drive to load XP. After loading XP I slaved my wife's hard drive and accessed her important files. I then disconnected the hard drives with XP and reconnected the hard drive with Ubuntu. Never had the Ubuntu hard drive and XP hard drives connected at the same time. When I try to boot Ubuntu from the hard drive I get the error message "missing operating system". My first guess is that it is a grub error, but it seems odd that grub would be messed up by the way I kept things isolated. Does bios play a part in this? I would be good to understand what went wrong with my logic, but the important thing is to get booted. Is my fix to re-install grub? I found several threads that deal with fixing grub, but wanted the opinions of others before proceding.

---

### Post by gsiliceo on 2008-01-20
In some bios you can change the order of your hard disk(ie. wich one boots first) it shouldnt be hard to find.

---

### Post by frup on 2008-01-20
Yeah looks like the bios can't find the drive to boot off. Did you connect it exactly the same as before (same cable etc)

---

### Post by paydaydaddy on 2008-01-20
You are absolutely right. While giving this thread a chance to be viewed and replied to, I did another search of the forums and found mention of a boot problem related to hard drive priority. I did a little looking around in the bios and found a way to check/change boot priority. Part of what I was doing with my wife's recovered files involved connecting an external hard drive. Bios decided to make the external hard drive the priority drive. Can't explain it, but it did. I reset the priority to the correct hard drive and, wala,  Houston, we have boot. Oh, many thanks for the quick replies.

---

