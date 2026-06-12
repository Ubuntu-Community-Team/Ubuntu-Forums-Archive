---
title: "Grub Confusing Me!!"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by RizingDamp on 2007-03-20
Hi Guys,

Well I aplogise beforehand for my question, because I am sure it has been asked a million times before. I have made searches, but with information gained I still do not feel confident enough with regard the installing, location of GRUB upon dual booting XP with Dapper Drake 6.06.  I have so far managed to resize my exisiting XP(ntfs) partiton using Gparted to allow space for installing DapperDrake.  In the remaining unallocated space I have created an ex3 primary partion for /root.  A FAT32 partion to be shared by both OS and an additional ex3 partion to be used as my home, (data) partion.  

My question being is that upon installing Dapper I will be asked where I want to install GRUB.  I have read that some place it in the MBR, whereas some say that this is a "NO NO".  Some say place it in the Linux root, but then when rebooting you get the message "operating sytem missing" because Im thinking grub has made the Linux partition the active partion, but with all the conflicting information I seem to have read Im becoming even more confused.....:confused: 


I would really appreciate your helping a complete noob on this, so I can get to installing Dapper Drake.:)

---

### Post by haricharan on 2007-03-20
placing GRUB in the MBR is safe and by default grub is written onto MBR...

---

### Post by mikewhatever on 2007-03-20
Having only one HDD, you should be fine following the default procedure. (installing GRUB to hd0, the MBR of your HDD) Things become more complicated when people have two or more HDDs, or need to boot numerous OSs. 
Grub is a sophisticated boot loader with lots of options. If you want to know more, check out [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Do expect it to be quite confusing.

PS: Have you also created a swap partition for Ubuntu?
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by RizingDamp on 2007-03-22
Thanks for the swift responses.

I followed the link to the physcocats site and read the following tutorial....

   [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

I have just 1 question with regard this install, I noticed that when it came to partitioning the /root partition, the bootable flag was left to "OFF"...is this correct as this is the install I am going to follow :) 




Andy.

---

