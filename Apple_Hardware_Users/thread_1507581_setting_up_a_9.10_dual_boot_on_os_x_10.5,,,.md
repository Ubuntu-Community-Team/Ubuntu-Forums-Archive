---
title: "setting up a 9.10 dual boot on os x 10.5,,,"
date: 2010-06-11
forum: Apple Hardware Users
---

### Post by zander1013 on 2010-06-11
hi,

i am attempting to setup a macbook run by os x 10.5 for dual boot with ubuntu 9.10.

however, when get the part where usually a gui interface which allows one to specify the size of the new ubuntu partition appears i only get the options for using the entire disk, the largest free space or manual partition.

how can i set this machine up for dual boot please?

thank you,

zander

---

### Post by Neds Moar Salt on 2010-06-13
> **zander1013 said:**
> hi,

i am attempting to setup a macbook run by os x 10.5 for dual boot with ubuntu 9.10.

however, when get the part where usually a gui interface which allows one to specify the size of the new ubuntu partition appears i only get the options for using the entire disk, the largest free space or manual partition.

how can i set this machine up for dual boot please?

thank you,

zander

Use manual to set up your partitions or Disk Utility/Boot Camp for repartitioning.

---

### Post by garvinrick4 on 2010-06-13
Is a lot more convenient to set up your partition first in gparted in live cd and then go to install from there, it is same CD. Use manual setup and just install the / into the partition you made. sdaX. and the X being the partition # you made. In the last page lower right hand corner is advanced tab, click on it and put grub into sda. Not sda1 or sda5 but sda. Do not need a swap if got a couple gigs of Ram all you need to do is put / in the sdaX that is yours for Ubuntu. / means your OS in Linux language. And Ubuntu likes ext4 format for the /.

Not sure with Apple but with Windows have to defrag a couple of times before taking a chunk of the drive for Linux. 

Start out in gparted by right clicking on main drive partition and resizing it to leave what you want for Linux. The part that is made for Linux right click on that and choose make
a Extended partition then right click on that Extended partition and choose make a Logical partition the size you want for Ubuntu. Anything left over in the Extended partition you can use at later 
date if you want to make another logical partition. Everytime you do something in gparted you have to click on the Apply green check mark on top the gparted page to apply it.

This I believe is about the cleanest way to set-up your drive. You will understand about Primary and Extended and Logical partitions if you read about them. And you will if you are going to partition your drives.

---

