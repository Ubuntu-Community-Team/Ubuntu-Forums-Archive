---
title: "Grub won't install on 2nd gen macbook"
date: 2011-06-05
forum: Apple Hardware Users
---

### Post by Mmarzex on 2011-06-05
I'm trying to install ubuntu on my 2nd gen MacBook the install goes fine up until it is trying to install grub and then it gives me an error saying it cAnt be installed to the partition of the install I try on other partitions on the hard drive but it still won't install. 

Now some background, I have my main os x system installed on a solid state drive with all the user files on a 500gb hard drive I partitioned the 500gb one to 400 for the user folder and about 100 for ubuntu. I don't know if maybe the way I have my hard drives setup may have something to do with it but I'm out of ideas at this point. 

I'm using refit as a boot loader but I just can't get grub to install so I can boot ubuntu.

---

### Post by linuxopjemac on 2011-06-05
I have Linux Mint 9 running on a MacBook 2nd gen. It is based on Ubuntu 10.04 LTS. I found that grub2, which is installed by default, sucks. I would go for legacy grub (grub1).
Boot from Ubuntu 9.04 liveCD and install Legacy Grub in the MBR (Master Boot Record, /dev/sda).

Good luck.
[https://help.ubuntu.com/community/DualBoot/Grub#Grub%20Legacy%20%28Ubuntu%209.04%20and%20earlier%20as%20well%20as%20upgraded%20to%209.10%29](https://help.ubuntu.com/community/DualBoot/Grub#Grub%20Legacy%20%28Ubuntu%209.04%20and%20earlier%20as%20well%20as%20upgraded%20to%209.10%29)

---

### Post by Mmarzex on 2011-06-05
I'll give that a try. Am I installing it to /dev/sda or /dev/sdb? sda is the solid state drive where os x is installed and sdb is where the partition for ubuntu and my user folder for os x is.

---

### Post by linuxopjemac on 2011-06-05
I would install it on /dev/sda then...if OSX boots from that drive.

---

### Post by Mmarzex on 2011-06-05
Thanks that worked.

---

### Post by linuxopjemac on 2011-06-06
Grub legacy, as you will notice, always works well. In the past I had Grub2 on my MacBook. It was horrible. Glad you got it working.

---

