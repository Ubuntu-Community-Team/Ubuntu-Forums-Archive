---
title: "Image of Ubuntu installation"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by jesrani on 2008-01-03
Hello all. I have installed Ubuntu 7.10 on an P2, 800Mhz machine with 312 Mb RAM. I want to shift this to new a new hardware and for this I had posted a thread on this forum. I got a reply that I can just put the HDD into a new machine and it will work. But just for safety sake, I want to make an image so that I can restore if something goes wrong. I have a 40Gb HDD partitioned into 15 and 25Gb with 25Gb being the /home partition. Please help how to do this.

---

### Post by foppeh on 2008-01-03
You might try [Remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys"). It will effectively make an installable DVD of your current setuol. I did make a backup, but I did not try putting it back on disk, so you may want to try before you delete  your old confugruationl.

Good luck

---

### Post by n8bounds on 2008-01-03
Try Partimage, it's easy to use in interative mode. 

If you have an entire drive spare you want to copy your root file system partition to as a backup, you can just just gparted and literally Copy the partition to an alternate drive.

But, yes, Linux is very portable, unlike Windows. Good luck.

---

### Post by Moop on 2008-01-03
Hi, You can use Partimage to backup your whole harddrive or partition. 

[http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")

---

### Post by jesrani on 2008-01-03
thanks for the reply everyone. i am downloading the System Rescus CD which contains PartImage and will give this a try. Should I backup only the main partition or also the /home partition? If I shift the disk to new machine, will there be any changes made in the /home partition.
Since this issue has come up, I have another question. My original HDD has 2 partitions + 1 for swap. The partitions are 15Gb main + 25Gb /home. I still have used only 4Gb and 10Gb respectively. Now if I make an image with PartImage, can I restore this to another HDD with different partition sizes, say 10Gb and 20Gb or say 20Gb and 60Gb?

---

### Post by jesrani on 2008-01-13
hello. i was able to finally able to run the system rescue cd after a bit of problem with startx. then I ran part image but was not able to understand how to put the image location. finally i think i understood. i have 2 hdd.
One is a 40gb having 2 partitions, one with my ubuntu 7.10 /root and the other with /home partition.
The other hdd is 80Gb single partition ext3.
I finally understood that I have to use mkdir command in terminal, then mount the 80Gb hdd here and then go to that dir and then run partimage. i did all this and ran partimage. then i boot from my 1st hdd with the valid Ubuntu 7.10 install. I mount the 80Gb hadd and I can see one lost+found folder and one file "Ubuntu_1.gz.000". Both have crosses over them and I cant open the file. What is wrong here??
I think partimage is good so I want to use it to make a backup of my install. Do I need to make an image of the /home partition also or can I do that in some other manner.
My 80Gb hdd is to be used for all backups. I am also starting another thread on how to backup files.

---

### Post by thomasr on 2008-01-13
Remastersys has worked well for me. 

Here are some nice directions:

[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

---

