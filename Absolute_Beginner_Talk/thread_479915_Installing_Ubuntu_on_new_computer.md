---
title: "Installing Ubuntu on new computer"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-06-20
I recently bought a new laptop (Sony Vaio VGN-FE870) and I want to install Ubuntu on it.  I've tried the live CD and all my hardware works, even wireless:D .  But I need to know a couple of things.  
1.  I want to dual boot with Vista.  Should I partition in Ubuntu or in Vista?
2. I have 2 GB of RAM; Is a swap partition still necessary?

---

### Post by p_quarles on 2007-06-20
1. You can do it either way, but it's much easier if you use Vista to free up space prior to installing Ubuntu. Vista doesn't get along with Ubuntu as well as XP did. 

2. I could be mistaken, but I believe that if you choose the "Guided partition" method during Ubuntu install, it automatically sets up a swap. To my understanding, this is a good thing, because Ubuntu will make use of that partition for many things even after you've installed it.

---

### Post by Sushubh on 2007-06-20
from my experience. partition in vista and install ubuntu later.

keeping a swap partition is always a safer option...

---

### Post by wormser on 2007-06-20
1.  You should defrag and shrink the vista partition in vista.  Use Ubuntu to format and create the swap.

2.  Yes you need a swap partition always.

[Use this guide.]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

---

### Post by Matt1632 on 2007-06-20
Ok, I usually have a seperate "home" partition.  However, I already have two partitions for windows on my disk.  How can I have more than 4 partitions?
Also, I wanted to know: how do I preform a command on a directory or file with spaces in the name?

---

### Post by Sushubh on 2007-06-20
umm u can have a lot more partitions than just 4 on your drive.... :)

---

### Post by Matt1632 on 2007-06-20
Really? I thought there was a limit of 4.

---

### Post by Sushubh on 2007-06-20
a motherboard has 4 IDE ports. so i guess 4 hard disk is a limit... :| without any additional hardware i assume...

---

### Post by wormser on 2007-06-20
> **Matt1632 said:**
> Ok, I usually have a seperate "home" partition.  However, I already have two partitions for windows on my disk.  How can I have more than 4 partitions?
Also, I wanted to know: how do I preform a command on a directory or file with spaces in the name?

Use a \ before the space.

Make extended partitions within the primary partition.  First in vista defrag and shrink the partition.  Then boot into the live cd and install.  In the empty partition make it a primary then create extended partitions in that primary.  Format the partitions.  The only tricky part is with grub and vista.  This [guide]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") should help you with that.

---

### Post by wormser on 2007-06-20
> **Matt1632 said:**
> Really? I thought there was a limit of 4.

You can only have 4 primary partitions, BUT you can create extended partitions in a primary partition to get around the limit.

---

### Post by jimrz on 2007-06-20
> **Matt1632 said:**
> Really? I thought there was a limit of 4.

it is, but one of them can be an "extended" partition which can contain many additional partitions within it. your laptop probably already has 2 partitions (1 = "vista" + 1 preinstalled by sony with their recovery data or whatever),. i would, after shrinking the vista partition, create a "primary" for / and then an "extended" consisting of the remainder of the drive which you can then create your /home + swap + whatever else you need within.

---

