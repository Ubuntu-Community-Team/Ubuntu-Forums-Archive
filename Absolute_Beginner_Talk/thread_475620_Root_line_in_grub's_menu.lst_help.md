---
title: "Root line in grub's menu.lst help"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-06-16
There is a line in menu.lst that starts with "root (hd0,x)"

If I understand right this points to the actual partition number on HD0 right?

How do I get a list of the actual partition numbers?  I can find the partition info like sda3, sda1, sda4 whatever, but not the actual partition number.

I have one partition that I need to add to grub, I know ubuntu lists it as sda6, but I need to find the right root entry.  Is there some sort of command line app I can run to get a list of all the partitions.  Using fdisk -l simply gives me the list as /dev/sda1, dev/sda2 ... and says that "Partition table entries are not in disk order"

If I can get this last partition working I'll be in 7th heaven!

---

### Post by jimbob on 2007-06-16
Usually you can be safe by subtracting 1 from the sda-number - ie sda6 would be denoted as (hd0,5) on your root line since grub starts counting from zero.

Go into grub in a terminal and enter *[COLOR="RoyalBlue"]find /boot/grub/stage1[/COLOR]*

This will give you all the hd-numbers of your bootable partitions even if you have multiple HDDs.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

