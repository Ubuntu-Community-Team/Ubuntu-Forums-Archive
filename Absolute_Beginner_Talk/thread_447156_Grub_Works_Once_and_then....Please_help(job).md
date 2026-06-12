---
title: "Grub Works Once and then....Please help(job)"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by dudahl84 on 2007-05-17
Hello everyone.  

I work as a tech for a school district.  After reading about ubuntu I decided to try it out on my test machine(comprised of spare parts).  That machine was running xp pro on a single partition 200gig hard drive.  Ubuntu installed perfectly on the first try by doing the guided resize install.  I told myco-worker(open source skeptic)  we should consider this as a money saver ($750,000 budget defecit, 2,000 computers being imaged this summer, licensing renewals, etc...)  

I have a mpct2300 with a 40gb drive(1 partition, xp) that I use for the majority of my work,travel and personal use.   I have tried  installing ubuntu to dual boot just like my test machine.  Tried every single install option for the one disk and tried everything with two disks including switching primary and slave jumpers & bios settings.  Initial problem was xp would not be listed in GRUB's boot menu.  Googled the problem and found my answer.  fixed the menu.lst file....rebooted.....both are listed.....happy happy joy joy!!!!  so i shut it down from windows and start it back up, bam....grub tries to load and the pc is thrown into a never ending cycle of restarting and attemting to load grub.  Im assuming The MBR is currupted, but how???? 

When using the 2 drive method I did both installs with the other drive unhooked so that ubuntu wouldnt force grub into the MBR...

---

### Post by dudahl84 on 2007-05-17
call me a newb....help

---

