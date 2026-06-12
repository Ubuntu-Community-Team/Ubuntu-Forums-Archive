---
title: "[SOLVED] Truecrypt Reiserfs Filesystem"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2008-03-06
I set up an encrypted device with Truecrypt as Fat32 since that was the only option, but I've been 
attempting to format it as Reiserfs ever since. I tried unmounting the drive and using the command, 
sudo mkfs.reiserfs /dev/loop0 and it looks to work, but the device remains fat32 when I remount it. 
What am I missing on this process?

Thanks for your help!

---

### Post by shanepardue on 2008-03-06
> **shanepardue said:**
> I set up an encrypted device with Truecrypt as Fat32 since that was the only option, but I've been 
attempting to format it as Reiserfs ever since. I tried unmounting the drive and using the command, 
sudo mkfs.reiserfs /dev/loop0 and it looks to work, but the device remains fat32 when I remount it. 
What am I missing on this process?

Thanks for your help!
I used this command before the mkfs one..

truecrypt /dev/sda1 --filesystem=none

That did the trick!

---

