---
title: "Honey, I shrunk the partition ..."
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by jimbob on 2006-05-19
I need to shrink my XP partition on my laptop and was wondering which software package you would recommend for the job.

I did this once long ago using canned instructions from a RedHat forum and it seemed to work, but now it appears there are better things with GUI's out there.

Would Gparted do the job OK?
________________________________       
  If I can't be Mr. Root I won't play ...

___________________________________
AMD 64 Sempron 3400+ 512MB 60GB
Gigabyte GA-K8NS socket 754 nForce3 250 chipset
nVidia GeForce2 MX/MX400 64 MB

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by aysiu on 2006-05-19
GParted or QTParted will *probably* do the job, but [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) is the only sure-bet I've encountered.

---

### Post by mcduck on 2006-05-19
I actually recommend using Ubuntu's install CD. Works perfectly :D

Just run defrag in windows safe mode couple of times before resizing the win partition.

---

### Post by louis_nichols on 2006-05-19
sure! just download an ubuntu livecd and gparted will be right there to do the job for you.

still... I'm not sure it can actually shrink a NTFS partition and at the same time keeping data on it :(

I think Partition Magic is the only tool that can use that... I might be wrong.

---

### Post by aysiu on 2006-05-19
If you're planning to use Dapper Drake, go here:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

Otherwise, if you're using Breezy, go here:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by aysiu on 2006-05-19
[QUOTE=louis_nichols]
still... I'm not sure it can actually shrink a NTFS partition and at the same time keeping data on it :([/QUOTE] GParted, QTParted, Ubuntu's installer, and DiskDrake can all do this.

Nevertheless, it's **always** a good idea to back up your data and defragment first.

---

### Post by catlett on 2006-05-19
May I ask why? Is it for installation or another reason? I ask because the installer can resize and install Ubuntu for you if you want. There is an option at partitioning that does a "default" resize and install. Meaning it takes a set amount of space from the windows aprtition. You can't choose the size, at least I don't remember getting the option. 
If this isn't the reason, disregard. 
My vote is for Partition Magic from windows if you don't mind paying for it. I've done things to my drive with PM that should be illegal and never corrupted or lost anything. It can definately resize ntfs without data loss. I've actually converted from ntfs to fat32 without data loss and converted from fat32 to ntfs without data loss with PM. You just need plenty of empty disk space to do it.

---

