---
title: "Missing partition"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by madhu.rox on 2006-10-10
I wanted to install ubuntu in my windowsXp home PC and dual boot it.when the installer asked me to partion my disk for a swap and a root, i did so and ended up in an error and also the installer crashed.now the other partitiion which i made empty with 20gb has dissapeared. Pls help help me.Did the Installer do a Physical damage?:(

---

### Post by jorn on 2006-10-10
Are you still able to boot into xp?

---

### Post by petri on 2006-10-10
Physical damage? No.

20GB vanished? Do you mean you don't see it in windows? That is alright, windows can't "see" Linux partitions but Linux can read **everything** on windows (fat, ntfs) partitions ;)

If you can boot into XP then you can do an install again. This time use Gparted in Live-session to check out your partition how it looks and maybe format it to ext3 if needed. Gparted you should find at System > Administration > Gnome partitiontool (or something). If you can't boot into widows you can still install Ubuntu again as above but first you have to fix your MBR. You find a guide to it here: [http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd](http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd)

You should have done a defragmentation before trying to resize ntfs partition but it might be too late for that now. Windows needs atleast about 20% more than it's actual size.

---

### Post by madhu.rox on 2006-10-11
ya fine i insatlled,n it works fine thanks,i used the disk manager to partition and it's cool,thanx guys

---

