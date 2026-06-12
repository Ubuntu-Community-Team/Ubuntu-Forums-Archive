---
title: "retrieving data on my harddrive"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by tocilog on 2007-03-10
ok so i screwed up my harddrive while partitioning. nothing valuable there so thats good, just my music n stuff. alot of music. as much as possible i dont wanna go through putting every song on there again when i think i can still scrounge for it. im running the dapper drake live cd on the laptop now. 

dunno if this helps so here it goes: 

```
sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1442    11574832+  83  Linux
/dev/hda2            1442        2432     7960176    5  Extended
/dev/hda5            2340        2432      746991   82  Linux swap / Solaris
/dev/hda6            1442        2339     7213090+  83  Linux

Partition table entries are not in disk order

```

so how does one go about getting stuff off the harddrive?

---

### Post by brettg on 2007-03-10
You haven't really provided enough info for a conclusive answer to be provided. As it is there are two possible scenarios here.

Scenario one (most likely) is that you have removed your original partition(s) and then created new ones on the same drive. If you did indeed do this then you cannot recover your data short of taking the drive to a forensic data recovery service and paying them large amounts of money to extract it for you.

On the other hand, scenario two is where your original partition remains intact and is one of the partitions present in the list you provided. In the unlikely case that this is true, you simply need to mount the relevant partition and access it as you would any other partition.

---

### Post by tocilog on 2007-03-10
ok, well heres what i tried. i went to the System->Admin->Disks->Properties tab. At the bottom was "Status: Inaccessible." with the button Enable next to it. I pressed that, and the Browse Button lit up. Pressed the browse button, nothing happened. I tried going to terminal but it said something like "Error, file doesnt exist." so i restarted. On that same tab it says "Access Path: None" What should I change it to? I went through the folders but i still cant find my original ones.

im gonna mess with it somemore i guess.

---

### Post by tocilog on 2007-03-10
alrighty, found my junk. just put "/root" as the Access Path. thanks for ur help brettg

---

### Post by tocilog on 2007-03-10
heh, i got one more question before im out of here: how do i go about installing a fresh distro without writing over my stuff? Also when the distro is installed, how to i make the data available. i can find my stuff using the live cd fine, but i cant change save anything on that side of the partition.

---

### Post by lukem on 2007-03-10
Your only safe bet is to connect an external drive and copy your music onto that while you can still get to it.

---

### Post by tocilog on 2007-03-10
alright, thanks ill do that.

---

### Post by tocilog on 2007-03-12
new problem. in one of my folders, it has a red X in the corner of the icon. Looking at the properties it says that some of the files are unreadable. going into the folder it shows no files at all. so does that mean that folder is gone for good?

---

### Post by az on 2007-03-12
> **brettg said:**
> 
Scenario one (most likely) is that you have removed your original partition(s) and then created new ones on the same drive. If you did indeed do this then you cannot recover your data short of taking the drive to a forensic data recovery service and paying them large amounts of money to extract it for you.


Not true.

sudo apt-get install foremost

Foremost is a command-line tool that you can run from the live cd.  You can get all the files that are not currupted off the drive, regardless of whether they belong to a partition or not.

Just because you bork your partition table does not mean you overwrote the data.

> **tocilog said:**
> new problem. in one of my folders, it has a red X in the corner of the icon. Looking at the properties it says that some of the files are unreadable. going into the folder it shows no files at all. so does that mean that folder is gone for good?

Can you access them as root?  They may have root permissions, in which case they would show up in the file manager, but you cannot touch them.

sudo nautilus

---

### Post by tocilog on 2007-03-12
> **az said:**
> Not true.

sudo apt-get install foremost

Foremost is a command-line tool that you can run from the live cd.  You can get all the files that are not currupted off the drive, regardless of whether they belong to a partition or not.

Just because you bork your partition table does not mean you overwrote the data.

tried iT. this is what i got:

```
ubuntu@ubuntu:~$ sudo apt-get install foremost
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package foremost
```



> Can you access them as root?  They may have root permissions, in which case they would show up in the file manager, but you cannot touch them.

sudo nautilus

i cant access these files by root. its just the folder that supposedly has them in there that i can see.

---

### Post by az on 2007-03-12
> **tocilog said:**
> tried iT. this is what i got:

```
ubuntu@ubuntu:~$ sudo apt-get install foremost
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package foremost
```



Foremost is in the universe repository.  I recommend the version in Edgy or Feisty.  The one in Dapper is not as easy to use - you can compile it from source from upstream if you only have a Dapper live cd to run off .

---

