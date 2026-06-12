---
title: "How to reinstall OSX over Ubuntu on a mac?"
date: 2011-08-24
forum: Apple Hardware Users
---

### Post by mannaro85 on 2011-08-24
Hi all,

I have a Mac Book with Ubuntu installed (no partitions). Do you know how to substitute Ubuntu with Leopard/Snow Leopard? My problem is that the OSX installation CD does not see my hard disk :p. Many thanks!

---

### Post by handy on 2011-08-24
You could boot with the Ubuntu LiveCD & then use GParted to format your drive as HFS+ after that when you install your OSX CD it will see it & do its thing.

---

### Post by srs5694 on 2011-08-24
You almost certainly *do* have partitions on your disk; however, you might have just one or two partitions, for the Linux root (/) filesystem and possibly swap. If it's a Linux-only installation, it's possible that your disk uses the Master Boot Record (MBR) partitioning system rather than the GUID Partition Table (GPT) that Mac OS X expects, at least on Intel-based Macs. (If it's a PowerPC Mac, then your disk almost certainly uses the Apple Partition Map (APM) instead of either MBR or GPT.) If you just convert from Linux filesystem(s) to HFS+ without changing from MBR to GPT, Mac OS X will refuse to install on your disk. Also, I've found that OS X sometimes refuses to install on HFS+ created by GParted.

For these reasons, I recommend you delete all your partitions and either wipe the MBR or GPT data or create new GPT data structures, then let the OS X installer create new partitions and filesystems. You can do this in several different ways:


[list]
[*]Don't do anything from Linux; just launch the OS X installation disc and, when you get a menu bar at the top, launch Disk Utility from the appropriate menu. (I don't recall which one it is.) You can use Disk Utility to partition the disk using a new scheme. There's an option in there to select from MBR, APM, and GPT options, but I don't recall the exact buttons you press to get to those options. I think it's an "advanced" or "options" button on the partitioning tab of the utility.
[*]Launch GParted from an Ubuntu live CD or other emergency disk, select Device->Create Partition Table, click Advanced, select "gpt" as the partition table type, and click Apply. This will create a blank GUID partition table. When you install OS X, it should be able to create new partitions, but you'll probably need to use Disk Utility in OS X to create new partition(s), as above. The only advantage to this method is that you won't need to specify the partition table type.
[*]Start and Ubuntu live CD, open a terminal window, type "sudo apt-get install gdisk", type "sudo sgdisk -Z /dev/sda" (assuming /dev/sda is the disk you want to wipe), and reboot into the OS X installer. The "sgdisk -Z" command wipes all MBR and GPT data, so you can then create new partitions in OS X. I *think* that you'll need to do this manually in Disk Utility, but it's conceivable that the installer will do it automatically. If the OS X installer creates partitions automatically, this will be a little quicker and easier once in the OS X installer, but otherwise it has no advantages over the other methods.
[/list]


If you've got a PowerPC-based Mac, you could do similar things, but you'll need to create an APM partition table rather than GPT.

---

### Post by handy on 2011-08-24
Good reply srs5694.

I've bookmarked it for future use. I wonder if you ought to add it to the wiki?

---

### Post by mannaro85 on 2011-08-26
Hi, thanks for the tips! After many attempts with gparted, I solved the problem formatting the hard drive using the OSX installation disc and then following the standard installation process :guitar:

---

