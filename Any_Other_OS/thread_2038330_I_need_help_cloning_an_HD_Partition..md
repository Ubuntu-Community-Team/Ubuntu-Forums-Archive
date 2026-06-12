---
title: "I need help cloning an HD Partition."
date: 2012-08-06
forum: Any Other OS
---

### Post by Orange_Ribbon on 2012-08-06
Okay,  so I used a Live disk on USB with GParted.  I copied the windows partition to the free partition on a separate HD and re-installed GRUB because I couldn't remember how to manually add something to GRUB.  OHHh and the partition that I copied to was larger than the original one. 

It recognized and booted to the windows log on.  It didn't copy some user settings and kept crashing when I logged on.  I wasn't sure if I have to manually copy something (also what would I have to copy?)  

I need this for work because my PC has an odd program that is took 3 hours on tech support to install.  Worse thing is I can't re-install it if something happens because the tec has to put in security information so each time it is installed it will cost us 200 ish because they charge 70 or 80 an hour.  I figured it would be better to have a back up HD with it already installed.

---

### Post by oldfred on 2012-08-06
Moved to other OS since it is really a Windows issue.

Windows is designed to only work from the partition it is installed into on the same computer. It does some checks to make sure it is the same computer, but writes some hidden serial number info in the MBR, and every PBR (partition boot sector)  has info on the partition it is installed into including start & size. Also in Linux cloning a drive creates duplicate UUIDs, I think if Window Vista or newer the BCD will have two partitions with the same UUID to try to boot from. If XP you have to update boot.ini with new drive & partition info. Also Windows only boots from primary NTFS partitions with the boot flag. Grub does not use boot flag either for Linux nor chainloading to Windows.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Mark Phelps on 2012-08-06
Realize it''s of little help now, but in future, if you need to copy an MS Windows partition, you would do better to use a Windows app like Macrium Reflect (which is free) or Acronis True Image.  They will image off the partition(s) and produce an exact copy on another drive.

---

