---
title: "How to reinstall Ubuntu in partition"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by quasismart on 2007-01-05
I need to reinstall Ubuntu on my laptop. The HD has been partitioned for Ubuntu, Ubuntu (Recovery) and Windowz. I would like to know if there is a way to reinstall Ubuntu onto the partition that it is currently in without messing up the ther partitions. I have a Breezy-custom.iso CD for installation.Could someone please give me some advice.

Quasismart says smart people can do dumb things to!!

---

### Post by jvc26 on 2007-01-05
Well - first Q any reason why you're using breezy rather than dapper or edgy? You can get hold of a new iso and then you have the latest version which may well assist you in running things. Secondly it should merely be a matter of sticking the burnt iso cd in, getting to the bit where you select the partitioning - go manually edit partition table, then find the partition you want to install it to, select it, format it and install :)
Il

---

### Post by CroEragon on 2007-01-05
You will get grub error. I just deleted my Ubuntu partition and installed it again on unallocated space and i got grub error (i don't know number). I dont know proper way to reinstall Ubuntu, Bulldog from this forum edited menu.lst so it points on my new installation and it works now.
You can take look at thread where bulldog helped me [here]("http://www.ubuntuforums.org/showthread.php?t=315569")

---

### Post by kingmonkey on 2007-01-05
when re-installing make sure that you **dont select** the delete whole partition table option.

Instead make sure / is assigned to the partition you want to install it to.

EDIT:

There shouldnt be any grub errors if you install to the same partition as before.

---

### Post by CroEragon on 2007-01-05
There will be if he just delete Ubuntu partition. I don't know about using installer but you can take look at thread for yourself and see.

---

### Post by quasismart on 2007-01-05
I am using Breezy because that is what my school required. I will upgrade after I get Breezy going again. I left another post title "error message" a few minutes ago that explains my problem in more detail. Could you please take a look at that?

---

