---
title: "Automounting a second hard drive"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Orochi on 2007-07-18
I have a second internal hard drive in my computer with two directories. I want to set it up so that when my computer boots up the drive is mounted and the two directories are bound to two different locations (so it would be the same as if I had called 'mount /dev/drive /drive' and then 'mount --bind /drive/dir1 /newdir' and 'mount --bind /drive/dir2 /newdir2'). I know how to setup fstab to mount the drive on boot, but I'm not sure how to get the bind command to also run automatically.

---

### Post by Happy_Man on 2007-07-18
Just add it to your startup commands. Go to System --> Preferences --> Sessions and in the startup programs tab, add an entry for those commands. It'll run every time you log in, no hassle!

---

