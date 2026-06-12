---
title: "How to install Ubuntu and XP"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by rausuar on 2007-03-05
Hi, I would like to ask, I am new for Ubuntu, and I have my computer with Windows XP Home, I would like to know how to install Ubuntu without touching the Windows XP, and on booting, decide which one to boot with.  Also I would like to know, that, as I would have to create a new partition to use Ubuntu, which program do you recommend to use to create such partition as easily as possible. - Raul

---

### Post by rjfioravanti on 2007-03-05
> **rausuar said:**
> Hi, I would like to ask, I am new for Ubuntu, and I have my computer with Windows XP Home, I would like to know how to install Ubuntu without touching the Windows XP, and on booting, decide which one to boot with.  Also I would like to know, that, as I would have to create a new partition to use Ubuntu, which program do you recommend to use to create such partition as easily as possible. - Raul

Just install ubuntu, there are options in the installer to not touch your existing stuff. You will be presented with a boot screen at startup to choose which OS, installer has its own partitioner

---

### Post by Matt1632 on 2007-03-05
Check out [http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/").  It has a lot of information.  The program for partitioning is called GParted, the ubuntu desktop cd graphical installer will guide you through it.

---

### Post by xyz on 2007-03-05
Here is one of the many HowTo's:
[Illustrated Dual Boot Site]("/boot/grub/menu.lst")
Good luck and Welcome here!

---

### Post by webofunni on 2007-03-05
i think you need to find a windows partition with lot of free space then split that partition. Your partition shoud have a space grater than 2gb for ubuntu dont assign any filesystem for your new partition(its better to keep that as unallocated space by deleting the new partition). Insert the live cd and start install when you reach the partition portion check manual partition then select the unallocated space ubuntu will create swap and ext3 partition 4 u

---

### Post by maniacmusician on 2007-03-05
> **webofunni said:**
> i think you need to find a windows partition with lot of free space then split that partition. Your partition shoud have a space grater than 2gb for ubuntu dont assign any filesystem for your new partition(its better to keep that as unallocated space by deleting the new partition). Insert the live cd and start install when you reach the partition portion check manual partition then select the unallocated space ubuntu will create swap and ext3 partition 4 u
yup, do as webofunni said.

Also, make sure to defrag your Windows partition multiple times before doing this, so that you minimize any chance of data loss.

You safest bet is actually to add another hard drive/external hard drive and install to that. It's the safest way. But if you're careful, you can also manage resizing your windows partition and installing them both on the same drive.

---

### Post by rausuar on 2007-03-05
Hey guys, thanks a lot for the help! I managed to install the Ubuntu and the Win XP without any data loss or problems! now I am trying to discover how to configure a PPPoE connection in Ubuntu.

Thanks! 

- Raul

---

