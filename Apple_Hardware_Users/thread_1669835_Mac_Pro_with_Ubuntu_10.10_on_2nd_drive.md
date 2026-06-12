---
title: "Mac Pro with Ubuntu 10.10 on 2nd drive"
date: 2011-01-18
forum: Apple Hardware Users
---

### Post by GeoffRoynon on 2011-01-18
I've finally managed to install Ubuntu on my Mac Pro after a lot of trial and error and thought others may benefit from my experience.
I bought a second internal drive (500GB) for my Mac Pro specifically to run Linux. I followed the instructions in this thread and other places on the internet but could not get Ubuntu to boot successfully once installed - it always hung on the flashing cursor in the top left corner.
Eventually I simply swapped the two internal drives (easy to do with a Mac Pro), reinstalled Ubuntu on the first drive (originally the second drive) and it booted up first time.

If anyone else is having problems installing on a second drive, swap them around and see if it works!

Thanks for a great forum :D

---

### Post by ZeroLinux on 2011-01-18
It is a very strange decision to swap drives. Did you install rEFIt on the first drive? Is should have seen grub loader and the /boot on second drive if you used ext2,3,4 filesystem.

---

### Post by GeoffRoynon on 2011-01-19
> **ZeroLinux said:**
> It is a very strange decision to swap drives. Did you install rEFIt on the first drive? Is should have seen grub loader and the /boot on second drive if you used ext2,3,4 filesystem.

I had rEFIt installed on the first drive but it still wouldn't boot. I used EXT4 for the Linux partition.
Swapping drives on the Mac Pro is easy and everything booted fine once I installed rEFIt on the new first drive.

---

