---
title: "Problem with Partitioning"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by guitarfreak2765 on 2007-12-10
So I'm using GParted for the first time. I'm actually using Linux period for the first time. I'm wanting to run a dual boot system, and went to make the partitions. For some reason, I can't modify the size of the OS. 

My screen has:
/dev/hda1        fat16      54.88MiB
/dev/hda2        ntfs        10.00GiB    RECOVERY
/dev/hda3        ntfs        99.74GiB    OS
/dev/hda4     extended   2.00GiB   
      unallocated     unallocated    1.00MiB
      /dev/hda5        fat32             2.00GiB



/dev/hda3 for some reason has what looks like a caution sign next to it, and I have no idea why. I can't modify it at all. And thinking about it, I'm not really sure how I want to divide all this up for a dual boot.

---

### Post by ekimregnirps on 2007-12-10
Awesome that you are using Linux for the first time. Once you get the hang of it, it rock anytime else. Anywayz...

   You are going to need to free up some free space before you can dual boot UBuntu/Windows. I don't think you can resize a NTFS parition from within the LiveCD, maybe with QTparted. (?) I used Parition Magic 8, to do my resize in WindowsXP. It does the job. Another idea would be to move the data from hda4 to another parition, then install ubuntu on hd4.
 best of luck

---

