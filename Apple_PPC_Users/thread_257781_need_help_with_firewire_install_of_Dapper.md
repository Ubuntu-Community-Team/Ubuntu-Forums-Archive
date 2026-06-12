---
title: "need help with firewire install of Dapper"
date: 2006-09-15
forum: Apple PPC Users
---

### Post by seatea on 2006-09-15
I want to put Dapper on a partition on my Iomega external firewire drive. I don't plan on using it as my primary booting OS, but expect I will boot it by holding down the option key and selecting it when I want to use it. I have OS X on the first partition of that drive and boot off it without problem. All my partitions on the  firewire drive are HFS+.I started to do the install off the Live CD and could find  the  partition, sda12, which is 40 gigabits, but the installer wants at least two partions, one for the swap space and one for the filesystem. I couldn't figure  out  what to do with the Live CD installer to get what  I needed out of the one partition. I am guessing it doesn't need a boot partition? 

I have Ubuntu Dapper installed on my internal hard drive.  Looking at my current install of Dapper on the internal hard drive, there are three partitions for my Linux setup comprised of:
1) boot, 2) file system, and 3) swap; in that order.

I did my original install of Linux on my internal hard drive from a single partition on that drive. I don't  remember now exactly how I did that and, in retrospect, I am grateful I even got it  installed. I went back with the old Breezy install CD to see if I could set up my external drive with it, but hesitated when I got to the partioning step. I think I originally deleted the HFS+ partition of the internal hard drive and then partitioned that segment  with the Breezy installer. Does that sound  right?

I am wondering if I should use the Breezy installer to set up the partition I set had aside on my external drive for Ubuntu and then run the Dapper installer or if I should try to use gparted to set up that partition for Dapper? Also, I keep thinking, is there a simpler way to set up that partition with the Dapper Live CD?

---

### Post by linear on 2006-09-16
It's not easy to boot Linux from an external Firewire drive. See this post for some info: [http://www.ubuntuforums.org/showpost...16&postcount=5]("http://www.ubuntuforums.org/showpost.php?p=498516&postcount=5")

---

### Post by seatea on 2006-09-17
After spending a couple of days looking at the  How to's on firewire installs, I am sorry to say that I can't make enough sense out of the process to attempt the techniques outlined. I think I will have to table my plans  for firewire booting of Ubuntu.

---

