---
title: "Moving windows to a smaller hard disk"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by iancg1 on 2007-01-18
Hey guys! I'm a total Linux noob so please bear with me!

Ok, I plan to install ubuntu on my PC. I currently have two hard disks, windows XP on the bigger disk and the smaller disk I use for miscellaneous files. Since I plan to make ubuntu my primary OS now but I still want to retain windows XP (since some programs I use still wont run on ubuntu), I want to transfer windows to the smaller hard disk. How do I go about this? Do I simply cut and paste windows to the other disk? How do I make the smaller disk the master disk?

Thanks all!

---

### Post by jvc26 on 2007-01-18
Are the two connected via the same IDE cable? If so its just a matter of switching the cable so that the master connector (the one at the end) is connected to the big drive, and the middle connector is on the little drive and the jumpers (little connector things on the back of the drive) are set to the pins which correspond to master and slave (which will be printed on the top of your drive casing. However by installing Ubuntu with GRUB to the MBR you can simply tell it where to boot from which will mean that the master/slave settings shouldnt be a problem.
I'm not sure it is possible to merely push the files from one drive to the other - I may be wrong but in the past Ive always had to install the OS to the drive I want, not merely copy the installer files across - especially as all the links in those files will then point to the wrong drive etc if you merely copy. Hence, you may have to reinstall windows first to the small drive then install ubuntu to the big one, write GRUB (the bootloader for ubuntu) to the MBR (master boot record, i.e. where BIOS looks to find the file it will load up the OSs from) and when you do that it should find the windows partition and add it to the bootloader.
I'd check out: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) which is really helpful on installing ubuntu :)
Il

---

### Post by jhenager on 2007-01-18
Windows is installed on the C: drive, it appears. If you moved that install to the other drive, (which would be D, I imagine), you would encounter errors unless you changed master to slave, and vice versa - mentioned above.
I'd do it in this order (after backing up any critical data to removable media).
1. Create image of current XP install using Parimage or Ghost.
2. Image smaller disk.
3. Swap IDE cable and jumpers on HDs to make current 'master' the 'slave' and the other way around. Verify that XP runs.
4. Install Ubuntu on slave disk, and choose option to erase all data on the larger drive.

---

### Post by hal10000 on 2007-01-18
@jhenager:
I'm almost sure you can't easily do point 2. from your advise if the windows partition to be backuped is bigger than the new disk where is has to be restored (at least not with patimage).
So, if the partition where windows ersides is bigger than the other harddrive you first have to resize the windows partition to an amount that fits to the size of the other harddrive.

---

