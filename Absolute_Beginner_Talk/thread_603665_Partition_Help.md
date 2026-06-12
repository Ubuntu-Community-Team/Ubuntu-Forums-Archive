---
title: "Partition Help"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Doyley on 2007-11-05
HI all,

I have two HDD, an 80GB and a 260GB.  On my 80GB I have Vista which I don't use anymore but I don't want to delete it just yet and I have Linux on my 260GB.  I would like to resize the 260GB HDD so that I can install XP for some dev work but I can't find a way to resize the partition and create a new one.  I have tried GParted which won't let me resize any partition.

Does anybody have any ideas?

Many thanks!!

---

### Post by rsambuca on 2007-11-05
You will need to use the gParted liveCD, or you can use the gParted from the Ubuntu live CD to do this.

---

### Post by az on 2007-11-05
I think you also need to turn off the swap partition since the live cd will use it if it can find one.  You should not be using anything on the disk you are partitioning.

sudo swapoff -a

---

### Post by Doyley on 2007-11-05
OK guys thanks for that.  In my stupidity I decided to see if the XP disk had the option of resizing the partition, so I put the disk in and without asking it has repaired my MBR or whatever it is so the boot menu doesn't come up anymore asking me what OS I would like to boot, it just boots up windows.  Does anybody know how to get it back?

I need to vent, if anybody is easily offended please don't read below...


I HATE YOU BILL GATES, IF I EVER LAY MY HANDS ON YOU I AM GOING TO INSTALL A COPY OF WINDOZE IN YOUR A***!!!!!!

Sorry about that, I feel better now.

---

### Post by rsambuca on 2007-11-05
You can just re-install Grub from any liveCD, but I thought you were going to re-install Gutsy anyways!

---

### Post by markusf21 on 2007-11-05
I had this problem in the past and SuperGrubDisk fixed it for me [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

