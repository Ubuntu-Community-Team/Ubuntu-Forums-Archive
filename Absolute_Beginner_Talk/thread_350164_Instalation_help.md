---
title: "Instalation help"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Staraloppan on 2007-01-31
I have XP media center, and i want to use it until i know ubuntu better, but i can not figure oute installing it, i have made an extra drive that contains 10GiB.... can anyone help me?

---

### Post by taurus on 2007-01-31
Here's a guide.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by jkeyes0 on 2007-01-31
If you are interested in becoming more familiar with Ubuntu, it might be a good idea to burn a copy of the CD (like you would to install it normally), then just reboot to it. It runs a full LiveCD environment that looks and feels identical to Ubuntu, but none of the changes you make actually impact your hard drive or Windows install (with the exception of hitting the "Install" button on the desktop.

---

### Post by viper on 2007-01-31
Go with the live cd and install on the 10 gig drive, then dual boot.
Make sure you backup any critical data in your win install just in case.......

---

### Post by Staraloppan on 2007-01-31
> **jkeyes0 said:**
> If you are interested in becoming more familiar with Ubuntu, it might be a good idea to burn a copy of the CD (like you would to install it normally), then just reboot to it. It runs a full LiveCD environment that looks and feels identical to Ubuntu, but none of the changes you make actually impact your hard drive or Windows install (with the exception of hitting the "Install" button on the desktop.

I have made an cd... but i can not find any of my files, ther for i want to install it and make a dual boot

---

### Post by housam on 2007-01-31
If you have the live CD , boot from it and choose to install. During the installation process when it comes to partitioning choose the manual way. this will give you the chance to partition the drive manually using the Gparted tool. devide the drive into 2 partitions : one for the root ( / ) ext format i.e. 9Gb and the other is for the swap ( swap format ) 1 Gb. then continue the rest of the installation steps.

---

### Post by jkeyes0 on 2007-01-31
> **Staraloppan said:**
> I have made an cd... but i can not find any of my files, ther for i want to install it and make a dual boot

It sounds like you're trying to access your Windows files from Ubuntu? In that case, you're going to have to do some special configurations. [Here's]("https://help.ubuntu.com/community/MountingWindowsPartitions#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971") a wiki article on how to do that.

---

### Post by Staraloppan on 2007-01-31
The problem is that my HD is in two pices but when i am looking ubuntu install there are 3, then i made another one....

---

### Post by Staraloppan on 2007-01-31
What shoud i chose? i want to use both XP mediaCenter and ubuntu!

If anyone has YM pls help me an guide me in chat

---

### Post by taurus on 2007-01-31
Did you look at the link that I included in your original thread?

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Staraloppan on 2007-01-31
> **taurus said:**
> Did you look at the link that I included in your original thread?

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Yes... but if you look at the picture i uploaded just now

---

### Post by taurus on 2007-01-31
From the link that I've provided, it shows you three options regarding partitioning.  Which one do you want to use?  If you already have partitioned your harddrive, then you would pick the third option.

---

### Post by hyper_ch on 2007-01-31
On that screenshot you posted, select "Manually edit partition table" and then please post the next screenshot :)

---

### Post by Staraloppan on 2007-01-31
what now? I want to use sda4

---

### Post by hyper_ch on 2007-01-31
Do you know what the 8 and 30 GB partitions are?

In order to get linux installed you need a second partition :)
For partition 4, you have a drop down menu there... can you expand that and tell what it is?

---

### Post by Staraloppan on 2007-01-31
8 GB do not know. 30 GB xp 325 gb misc

swap 
/
/home
/boot
/usr
/var

---

### Post by hyper_ch on 2007-01-31
please create another partition that is about 1.5x - 2x the size of your ram... if you have like 1GB ram then make it 2Gb....

After that select for the 10GB partition (sda4) the option "/" and select for the newly created 2Gb (or something like that partition) "swap"

---

### Post by hal10000 on 2007-01-31
You have a problem because you already have four primary partitions which is the maximum you can use on a harddrive.

You can't install ubuntu (or any other OS) without delete one of them.
Because ubuntu needs at least two more partitions (one for your system and one for a swap partition you have to create an extended partition in which you can then create up to 64 further so-called "logical partitions".

I would recomment first backup your data, then delete /dev/sda4, then create an extened partition and within the extended partition two logical partitions, one swap of about 1GB and the rest for your ubuntu sytem root ( / ) (ext3).
Then choose the "manually edit partition table" option and assign the new partitions manually to their mount points.

---

### Post by hyper_ch on 2007-01-31
Even if he has used 4 primary partitions now he can still add more logical ones... can't he?

---

### Post by chr on 2007-01-31
hi there,

just tick the button, which says manual partition. then you can set up the partitions on your harddisk, the way you want. grub will be installed automatically and when you reboot your pc after installing you can chose between xp and ubuntu.

chr.

---

### Post by hyper_ch on 2007-01-31
ok, hal10000 was right...

So delete that 10 GB primary partition... then created an extended partition and inside create a "ubuntu" partition (10GB) and a "swap" partition (1-2GB) as logical partitions.

---

### Post by lyceum on 2007-01-31
Correct me if I am wrong, btu if he is using 2 hard drives, shouldn't he see two hard drive options on the first pic he posted? And have the option to erase the one he wants to use?

-edit-

re-read, by drive he must mean partition(?)

---

### Post by hyper_ch on 2007-01-31
Why do you think he is using 2 hds? I only see sda listed

---

### Post by lyceum on 2007-01-31
> **sjau said:**
> Why do you think he is using 2 hds? I only see sda listed

In the origanal post he used the word "drive", not "partition" Hence the edit. Sorry. That is how my brain prossess the words, drive for hard drives, partitions for partions within the hard drive.

---

### Post by hal10000 on 2007-01-31
> In the origanal post he used the word "drive", not "partition" Hence the edit. Sorry. That is how my brain prossess the words, drive for hard drives, partitions for partions within the hard drive.

You're right. So you can just select the other harddive in the upper-right box.

---

### Post by housam on 2007-01-31
> **sjau said:**
> Even if he has used 4 primary partitions now he can still add more logical ones... can't he?

No . he can use only **4 primary **partitions  OR  **3 primary **partitions and **one extended** partition which can be devided to many logical partitions.

---

### Post by Staraloppan on 2007-01-31
As i know of i onley have on HD, when i started the install to Ubuntu for the first time, there was allredey 3 sections, and i onley know of 2, that is what i can see on my XP explorer... pls advice

---

### Post by hyper_ch on 2007-01-31
Staraloppan:

Delete that 10GB partition that you created.
Then create a new EXTENDED partition.
In that EXTENDED partition you can then create 2 logical partitions.
Make the first one the double of your ram size and use the rest for the other partition.

---

### Post by Staraloppan on 2007-02-02
How do i create extended partisions?

---

### Post by hal10000 on 2007-02-11
> How do i create extended partisions
Open your partitioning program (i suppose it is gparted) and instead of the default selection (ext3)  choose "Extended".

---

