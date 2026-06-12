---
title: "Need help with Drive Integrity Test"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by iceshaft07 on 2006-07-19
Recently my computer crashed from browsing the internet, giving me GRUB ERROR 25, which is apparently a Disk Read Error, suggesting that my hard drive is failing.

I would like to perform the linux version of chkdsk /r, but I have no idea what I am doing.

From what I understand, I cannot run fsck on my drive while it is mounted, so I have to do the following:
1) Load up a live CD
2) Mount HDD0
3) Unmount HDD0
4) fsck HDD0

I got through step 1, but I can't seem to do any of the others..

sudo mount -t ext3 hdd0 /mnt
sudo unmount hdd0
fsck hdd0

Or, if there is a way to run fsck on start up,that is acceptable too.

Could someone please help me?

---

