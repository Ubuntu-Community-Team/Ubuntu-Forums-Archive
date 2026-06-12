---
title: "partition failure problem (Ubuntu install and Gparted)"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by bren on 2007-06-02
Hello

I am trying to install Ubuntu (7.04) on a Windows XP  laptop.
I downloaded the 386 install CD (even though i have AMD64 processor)
Having used Ubuntu (cd boot) for a couple of weeks I decided to install

I want to install Ubuntu to allow a dual boot system.
I have a 93GB drive with 37GB used and 53GB free

The error comes on the page where you choose what type of partition you want (about 3 screens into installation).    There are 3 standard options to choose from
- guided dual boot
- full hd install (wipe windoze)
- manual option

If I choose guided install for dual boot (option 1) it fails with a message that "An error occured"
Subsequently if i press back now only 2 options are available (full HD partition which I don't want) and manual parition which I don't understand.

Interestingly I tried to prepare a partition manually in Gparted - this gives exactly the same error.

Any helpful people out there?

Bren:(

---

### Post by jonward0690 on 2007-06-02
Go to option 3 and try to resize your win partition and make a swap twice the size of your ram then make your ubuntu partiton.

---

### Post by bren on 2007-06-02
Thanks jon

i already tried this
i went to manual
i selected main partion 
right clicked and tried to resize
same error - cannot resize main partition
any ideas?

---

### Post by bren on 2007-06-02
could try create partition in windows first?
would that help?

---

### Post by zvacet on 2007-06-02
It will be smart t ohave separate home partition.
1.root =10GB                                       mountpoint /
2. home =rest of free space exept        mountpoint /home
3.swap =2xRAM

---

### Post by bren on 2007-06-02
here is screen i get in gparted when trying to resize main (windows) partition
any ideas?

---

### Post by jonward0690 on 2007-06-02
Well All tell you this for some reason when I bought my pc I could not resize the Win partition with anything so I said forget it and deleted windows well I reinstalled windows because I didnt get the fill for linux tried them again and I could resize my win partitons.It was like Dell locked the Win partiton so you could not manipulate it.

---

### Post by bren on 2007-06-02
jon,

thanks for that - this machine is a fujitsu siemens laptop - i wonder if it has same prob as your dell

i will maybe try a windows partition program to see if is "locked"

i could use free demo of partition magic - anyone know other freeware for this

cheers
b

---

### Post by zvacet on 2007-06-02
Download Gparted live CD.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by bren on 2007-06-02
thanks zvacet 
but dont see how that would help
i already have gparted within Ubunto (running from CD only)
gparted fails when trying to do partition resize (as described above)
bren

---

### Post by nightspore on 2007-06-02
I had the same problem, and solved it by defragmenting my (very fragmented) windows drive.

---

### Post by ugm6hr on 2007-06-02
> **zvacet said:**
> Download Gparted live CD.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

I second this.  GParted on Ubuntu does not have the ability to resize NTFS partitions (check in menu GParted->Features).  The GParted LiveCD will manage it.  Just boot the GParted LiveCD (pick the second boot option).  It opens with newest GParted.

If you don't understand the Ubuntu manual install option, I would recommend you just shrink the Windows  partition (as it appears you were trying to do) in GParted LiveCD.  Leave the intended Ubuntu+Swap partition size unallocated.  Then when you boot the the Ubuntu LiveCD installer, it should give you a "guided" option to use the *largest continuous free space* (it did in Xubuntu7.04 anyway).  That will sort out your swap partition too.

If you want to plan ahead - think about making the "unallocated" Ubuntu+Swap about 10-20GB, and create another "data" partition to save files on (FAT32 is reasonable initially).  If you're going to go down this route, you will have just enough partitions to make them all primary rather than extended.

PS: defragmenting before running GParted is a good idea too.

---

### Post by bone43 on 2007-06-02
> **bren said:**
> thanks zvacet 
but dont see how that would help
i already have gparted within Ubunto (running from CD only)
gparted fails when trying to do partition resize (as described above)
bren


A few things make sure you defrag at least twice in windows before trying a resize i would try this first and/or it may also be you have some bad sectors on your drive ive had this problem before with gparted.

Probably the best way is to find out the condition of your drive is to get a disk check utility from your hardrive manufacture you can get this info from  windows device manager and then get the right disk check utility of the net and run it.

---

### Post by bren on 2007-06-02
thanks all for your suggestions

1) defrag - had done twice before starting thanks

2) gpart LIVE CD - worked!

now created following

windows partition ntfs 58GB

linux root 10GB
linux swap 2GB 

data FAT32 22GB

any comments?

about to start install again...;)

bren

---

### Post by bren on 2007-06-02
ok guys thanks for your help
finally got it installed

:D

although first time through install failed due to error on the cd (i ran the cd checker and it was ok so cleaned the cd and it worked second time)

---

### Post by zvacet on 2007-06-02
Wellcome to comunity.

---

