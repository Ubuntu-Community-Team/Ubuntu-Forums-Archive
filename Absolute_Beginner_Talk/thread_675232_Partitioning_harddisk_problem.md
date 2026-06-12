---
title: "Partitioning harddisk problem"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by tkn4everb on 2008-01-22
Hey guys me and my friend are having a problem trying to install linux. Whenever we get to the "prepare disk space"  page it only gives us three options

- Guided - use entire disk
- Guided - use the largest continous free space
- Manual

Theres supposed to be a slider that lets us choose how much space we want to partition, but it is not their. How do we fix this?

---

### Post by travis31 on 2008-01-22
You should select the Manual option to specify partition sizes
[https://help.ubuntu.com/community/forum/installation/Partitioning]("https://help.ubuntu.com/community/forum/installation/Partitioning")

---

### Post by stoneybroke on 2008-01-22
Are you going for a clean install or a dual boot system

---

### Post by tkn4everb on 2008-01-22
Thanks, we got it. For some reason we had to restart it and that seemed to work. Thanks again.

---

### Post by user1397 on 2008-01-22
> **tkn4everb said:**
> Hey guys me and my friend are having a problem trying to install linux. Whenever we get to the "prepare disk space"  page it only gives us three options

- Guided - use entire disk
- Guided - use the largest continous free space
- Manual

Theres supposed to be a slider that lets us choose how much space we want to partition, but it is not their. How do we fix this?
i think that feature, if there ever was such a feature, doesn't exist anymore.  just use manual partitioning, for any windows partitions (if you do not want to destroy them), don't mount them to anything, not even / (so basically leave the mount parts blank for any windows partitions).

then just select the amount you want for the linux partition, make sure you have a swap space parition, and you're good.

a good GUI partitioner you can opt to use instead of the one in the installer is the gparted app.  its in system > administration > gparted

---

### Post by tkn4everb on 2008-01-22
We ran into our second problem :(.
Whenever we try to use the terminal to install something it will ask us for the user password, but it wont let us type the password or anything in for that matter. Is their a way to disable ubuntu from asking us to put in a password?

---

### Post by Tanjer1588 on 2008-01-22
> **tkn4everb said:**
> We ran into our second problem :(.
Whenever we try to use the terminal to install something it will ask us for the user password, but it wont let us type the password or anything in for that matter. Is their a way to disable ubuntu from asking us to put in a password?

Im guessing your running it off of the live CD right? when you type in a password in ubuntu its set to show no text, but you are typeing. If your running off the live cd i dont think there should be a password on it... but im not shour how to change it, just try hitting enter without typeing anything in and see if it works.

---

### Post by user1397 on 2008-01-22
> **tkn4everb said:**
> We ran into our second problem :(.
Whenever we try to use the terminal to install something it will ask us for the user password, but it wont let us type the password or anything in for that matter. Is their a way to disable ubuntu from asking us to put in a password?do not reformat partitions while in a standard install of ubuntu; always use a live cd (aka the desktop cd) so no partitions are corrupted/harmed.

are you using a live cd?

---

### Post by 565Customz on 2008-01-23
how do you know if you have the live or standard...i think that may be my prob cuz im having trouble with partitioning too...

---

### Post by indytim on 2008-01-23
> how do you know if you have the live or standard.

A LiveCD is a CD you boot to (insert CD into your CD drive and bootup against the CD).

One of the recommendations stated above is:
1.  Get a copy copy of GParted Live [http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")
2.  Burn the downloaded .iso image as an iso to a CD.
3.  Bootup using GParted Live.
4.  Pre-Configure your partitions (at a minumum, you will need a small /swap (2x RAM) and one ext3 partition (~4-10G).
5.  Shutdown after you have configured your HD with the above.
6.  Re-Boot with the Ubuntu-Kubuntu-Ubuntu etc Live CD.
7.  Select the installation option.
8.  When you come to the point in the install re. the partition, select the Manual option.
9.  Identify the partition you set up as ext3 as your "/" option.
10.  Identify the /swap partition.
11.  Proceed with the balance of the installation.

IndyTim

---

