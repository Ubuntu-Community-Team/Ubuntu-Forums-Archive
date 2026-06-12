---
title: "Fail booting after redimensionning partitions"
date: 2010-11-08
forum: Apple Hardware Users
---

### Post by guguscat on 2010-11-08
Hello,

I am having a problem with Ubuntu boot on my macbookpro 5.5.

A week ago, I needed more space on my /home and I just discovered I had an other operating system installed on my computer which was taking lot of space and that I wasn't using anymore since ubuntu 10.04 and 10.10 works really well on my hardware. I decided to reduce the "other operating system" partition which I did using the os tool (which is "disk utility" in that case).
Then I moved the / partition to the left and expanded the /home using Gparted on an ubuntu live cd. All those operations went well.
I encountered a problem to boot Ubuntu when rebooting after that. I first though refit was the problem so I updated it from 1.12 to 1.14 but it didn't solve the problem.
I tried to reinstall GRUB on my / from a live cd which seemed to work.
In fact I appears that reinstalling GRUB works but just for one time (I don't reboot my computer very often). I just tried again reinstalling GRUB and I could run Ubuntu one time and that's all.

I don't know enough about EFI/rEFIT/GRUB so that's why I'm asking you if anyone understand the problem.

Before "partitionning" I had a 100 MB free space between my partitions and no more now. Maybe this is the problem source ?

Thanks in advance to anyone who could help me and I'm sorry if this has been already asked.

---

### Post by guguscat on 2010-11-11
I tried to add an free space of 150 MB between my partitions I didn't seemed to work. (I could boot only the first time)

I reinstalled my / from scratch with the livecd and it now works.
So it seems like I was not running the right command to install grub.

Does anyone knows the grub-install command ran by the installer ?

---

