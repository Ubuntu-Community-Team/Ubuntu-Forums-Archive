---
title: "[SOLVED] Boot hangs!  Help!!"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Speedoo on 2007-12-13
Hi all,
I've been running Gutsy since it came out a few months ago without any problems.  Today, though, when I tried to boot my computer, I get as far as "Running /scripts/init/bottom...", then "Done.", then nothing.  I'm able to boot from the Live CD, but can't find any of my files  (in the /home directory, I only see "ubuntu")  Naturally, this happened as I was trying to catch up on work (the thing always seems to work fine when you just want to play a game or browse the net!)  
Thanks for any suggestions!

---

### Post by dstew on 2007-12-13
Boot your LiveCD and run a file system check on the partition that contains your Ubuntu root directory:```
sudo fsck /dev/sda1
```Assuming that /dev/sda1 is the name of your Ubuntu partition.

---

### Post by xeth_delta on 2007-12-13
> **Speedoo said:**
> Hi all,
I've been running Gutsy since it came out a few months ago without any problems.  Today, though, when I tried to boot my computer, I get as far as "Running /scripts/init/bottom...", then "Done.", then nothing.  I'm able to boot from the Live CD, but can't find any of my files  (in the /home directory, I only see "ubuntu")  Naturally, this happened as I was trying to catch up on work (the thing always seems to work fine when you just want to play a game or browse the net!)  
Thanks for any suggestions!

The /home directory you see while booting from the cd (existent only in RAM memory) is not the same as the one you have on your hard-disk. If you want to check the state of your files, mount the respective partition.

Xeth

---

### Post by Speedoo on 2007-12-13
Thanks.  I did the fsck ) and it did find quite a few errors, which I allowed it to fix.  However, the boot still hangs at the same place.  I finally solved the problem by reinstalling Gutsy from the Live CD.  Now I just need to re-download and re-configure for a few weeks!
Nothing like the big hammer approach, huh?

---

