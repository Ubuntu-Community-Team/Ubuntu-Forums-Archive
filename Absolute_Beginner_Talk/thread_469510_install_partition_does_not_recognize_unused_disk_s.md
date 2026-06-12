---
title: "install partition does not recognize unused disk space (I think)"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by doobey on 2007-06-10
I am trying to  install liveCD onto my Dell Inspiron 1300 laptop with  22GB unused, with a dual boot setup.  During install, the partition part, I did not get a "guided re-size" option, only "use entire disk" or "use largest contigous space." This last option got an error message: "failed to partition or free space to small." (I defraged twice before attempting install.)

I'm guessing the problem is that install does not recognize the free space on my ntfs root partition, notice the sda2 line below.  used space is "unkown" (Later, fooling around I opened the GNOME partition editor. it recognized 22GB as unused).

Here is what the partition menu in install says:
/dev/sda1 fat16 /media/sda1 41MB(size)/ 33MB(used)
/dev/sda2 ntfs /media/sda2 36479MB/unkown
/dev/sda3 fat32 /media/sda3 3479MB/3100MB
free space 8MB

in GNOME all the partitions had lock icons next to them and most partition menu commands were grayed out.

I'm at a dead end. 

Thanks again for all the help!!!

---

### Post by doobey on 2007-06-10
Problem (almost) solved. My XP admin account was password protected. I removed it, rebooted, loaded liveCD and liveCD install partition recognized the free space. Tomorrow I will do the install. (I won't attempt it tonight after a couple of pints of beer...)

I still don't get the "Guided re-size" option. But this newbie just might try and re-size my /sda2 to 18GB in the "Manual" partition option,  leaving me a little under 18GB for Ubuntu.

If u think I am making a giant mistake... let me know!!!

d

---

