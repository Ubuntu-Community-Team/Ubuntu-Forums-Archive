---
title: "Frozen Screen"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-05-14
Finally I manged to load 32 bit Ubuntu 7.04 to my desktop after making a 2 GB SWAP partition using GParted.

It is Sempron 2500+, 256 MB RAM (Shared video RAM 32 MB, I had reduced it from 64 MB), Via Chipsets K8M800 and VT8237R.

The problem is that the machine hangs (multiple windows open, not many) after some time and I got to re boot.
ANY SUGGESTIONS why it is happening and how to correct ?


There is one more problem, it was there in my laptop too (see signature for specs), but vanished after I edited fstab to give r/w permissions to some partitions. Here it does not go.  On start up, after GRUB, I get message that"there is offset between Boot Sector and its Backup", then the offset values and finally "Not automatically fixing this". 

I have posted earlier, others have also faced the problem, are living with it, no explanation so far. Can anyone please help on this ?
ANY COMMENTS ?

---

### Post by Repabil on 2007-05-23
Do you find any errors or criticals if you look through System - Administration - System Log?

---

### Post by Sparkster185 on 2007-05-23
If you open up the System Monitor, is Xorg taking up a lot of CPU?  If so, it could be an issue with your graphics card/driver.

---

### Post by dptxp on 2007-05-26
Thanks.

The problem was video RAM. I had reduced it to 32 MB to give maximum to Live CD. Had not increased it after installation.

No frozen screen any more.

---

