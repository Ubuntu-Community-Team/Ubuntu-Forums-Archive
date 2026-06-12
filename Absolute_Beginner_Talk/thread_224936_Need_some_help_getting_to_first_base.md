---
title: "Need some help getting to first base"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by namrocks on 2006-07-28
I have been reading forum posts and documentation for 2 days and am now ready to do my first ever hard disk partition and have my first ever experience with a non-Microsoft OS. I'm not sure I fully understand what I am supposed to do so I would like to outline my game plan in the hopes that someone will be willing to let me know whether or not I am out to lunch. I have XP on a Dell laptop with a 40 gig hard drive with 22 gigs free and no partitions. When I am finished I hope to have a dual boot system with all of my current Windows apps and data intact. I want to allocate 8 gigs for Ubuntu including one gig for the swap drive partition. It is my understanding that when I reach the partitioner stage of the installation process that I should select the manual option. Since there are no partitions there will be only one drive option to partition. At that point I should select a smaller size which means I will select 32. That should reduce my current c: drive to 32 gigs and allocate 8 gigs for the new partition. I should then select “guided partitioning”. I am assuming at some point it will be obvious how to make an additional on gig partition for the swap drive. I am also assuming that once I make the new partition it will be obvious how to make sure that Ubuntu installs itself in that new partition. Well, does this game plan make sense? Thanks in advance for any help.

---

### Post by Tomosaur on 2006-07-28
That seems fine to me, but here's a few tips:

Back up all your critical data. NTFS is a closed format filesystem,  meaning the guys who make the partitioner used with the Ubuntu installer don't have access to the full workings of it. For this reason, it **can** mess up, as it did to me. I would definately recommend that you resize your windows partition from within windows, since mine messed up and I needed to reinstall windows completely.

Make a windows recovery CD. If anything does go wrong, try recovering your windows install rather than just reinstalling it completely. Makes sense.

The partitioner you will use during the installer works in MB, not GB. For this reason, remember the following:
Number of megabytes in a gigabyte: 1024.
Number of megabytes in 32 GB: 32768.
Number of megabytes in 8 GB: 8192.

Once your partitions are all set up, you'll be asked to set the mount points for linux. Don't panic, the installer should detect all of this automatically based on your partitions, and since you're only going to have a basic partition structure, you should have no problems. Still, for reference:
Your 8GB Partition should be set to '/'. This means 'root'.
Your 1GB Partition should be set to 'swap' (or 'linux swap').
Your 32GB Partition should be set to something like '/media/hda2', but if the line isn't blank, just leave it at whatever it is.

Once the install is complete and you've rebooted your system, you'll get a menu screen (this is actually a boot loader called GRUB), which will list your operating systems. Use the up and down arrows on your keyboard to select which you want to use. Ubuntu should be at the top, Windows should be at the bottom. Try  firing up windows to see if everything's ok. It should be fine, but better to check now rather than later. Once you're happy, reboot and fire up Ubuntu. Welcome to linux!

---

### Post by djsroknrol on 2006-07-28
Everything sounds good...I would suggest you use the GParted live CD for your partitioning as the partitioner on the install CD has been buggy for some. I use it with great results. I don't have a link for it, but you could Google it or someone might have a link for it (I'm not at my computer at the moment). Good luck to you...

---

### Post by confused57 on 2006-07-28
Here's some screenshots of the gparted live cd:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Get it here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

It's easy to use(30 Gb download)...I used it to set up partitions to install Mepis to dualboot with Dapper.

---

### Post by namrocks on 2006-07-29
Tomosaur - Thank you so much for providing just the sort of detail I was looking for to feel more confident about taking the plunge. I have also downloaded the GParted live cd per djsroknrol's suggestion. Your help is much appreciated.

---

