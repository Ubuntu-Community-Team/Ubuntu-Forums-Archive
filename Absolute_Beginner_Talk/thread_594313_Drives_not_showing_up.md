---
title: "Drives not showing up"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by asdoylejr on 2007-10-27
Just installed a fresh copy of 7.10 on a brand new harddrive on my Dell laptop.  Everything works fine except that 1) Ubuntu does not recognize my external hard drive, says it cannot mount it, and 2) it doesn't see my internal hard drive.  Both don't show up in the "media" folder in the filesystem.

I'm pretty new to Linux, and I did do a brief search for people with similar problems, and whatever I found did not seem to work.  Any ideas?  Thanks so much!

---

### Post by Pumalite on 2007-10-27
Post:
sudo fdisk -lu
mount

---

### Post by asdoylejr on 2007-10-27
That didn't work, that was one of the random remedies I found in the forums but failed.  I know the drive is fine because when I put in my Windows hard drive, Windows sees the drive and it's data fine.  Any other suggestions?

---

### Post by Pumalite on 2007-10-27
Make sure it's recognized in BIOS. Check connections. If it's a new drive, make sure it's formatted.

---

