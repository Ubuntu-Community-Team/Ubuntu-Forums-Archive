---
title: "loading linux kernel stuck"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by mike d on 2008-02-28
Trying to load 7.10 from CD first, before I install. Ultimately I would like to dual boot XP and Ubuntu. When I try to boot from CD I get "Loading Linux Kernel" stuck at 100%. After some research I read that this could take 15 minutes or so but I let it go half an hour and still no luck. I also found that entering "pci=nomsi" at the boot screen can also help this problem but still nothing. I installed Ubuntu on my HP easily and quickly. Any ideas as to why this is happening? ANY help greatly appreciated!

System:
Thinkpad R61 
Core 2 Duo
Windows XP
80GB HDD
1GB RAM

Ubuntu 7.10


PS. no peripherals attached

---

### Post by Origin415 on 2008-02-28
Make sure the disk you burned is good, there is a guide on checksums here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mike d on 2008-02-28
forgot to mention that. I did check to make sure the file was in tact after downloading. any suggestions?

---

### Post by Joeb454 on 2008-02-28
Did you verify the data on the disc after you'd burnt it?

---

### Post by mike d on 2008-03-05
I figured it out, here I was burning Ubuntu onto a CD-RW that had been erased and re-used. Apparently images don't work well with this strategy. After burning the same file to a new DVD everything worked fine. Thanks for the help!

---

