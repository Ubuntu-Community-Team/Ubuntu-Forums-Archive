---
title: "Automounting an second ext3 partition"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by TheThingfish42 on 2008-02-24
I just wiped out my windows partition the other day, and made it into a new ext3 partition, but every time I log into Ubuntu I have to remount it and enter my password. I am trying to use it as my main storage area. It is a partition from my main (and only) hard drive. I can access it after mounting it, and gave my self read/write permissions, but cannot find clear instructions to have it automount when I log in. I know I need to edit my fstab, but I do not know what to put in there. The partition that holds ubuntu and my filesystem is sda3, the new partition is sda1.  I want to be able to store things such as my primary download folder, various icons im using in the system background etc, but if it does not automount on log in, then of course ubuntu can't get at the stored data on log in, and I end up with a blank background and none of my goofy lil' icons hehe.

Ill be watching the post if more information is needed, but I would truly appreciate some help from a more experienced user :) 

Thank you very much for your time and assistance :)

---

### Post by RSLxH on 2008-02-24
It just needs to be added to your fstab file. There is agreat "Mount Linux" Guide on psychocats.net:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by ByteJuggler on 2008-02-24
Add the following line to your fstab:

```
/dev/sda1 /home/user/Data           ext3    defaults        0       2
```

The entries are respectively, from left to right:
1) The partition to mount
2) The place to mount it
3) The filesystem to use when mounting
4) The options to use 
5) Whether to include this filesystem when the "dump" command is run (can be ignored/set to 0 always)
6) The priority/order that fsck checks filesystems in.  The root filesystem has highest priorty, which is 1, other partitions are given higher numbers (meaning lower priority.)

If you'd like to use a UUID to identify the parition (instead of /dev/sda1) then you can use the following command: 

```
blkid
```

This will list the partitions and corresponding UUID's.  The line would then look something like the following:

```
UUID=52543cae-019c-41b8-b275-37d8a585a93e /home/user/Data           ext3    defaults        0       2
```

Obviously you have to change the mount point to where it needs to be.  

Aside:  If you want to have your home folder be on the other partition, then the best would be to log in as another user, then from that account move all the files over to the other partition while mounted somewhere else temporarily, after which you can set up the proper mount and log in again.  (If you're going to do that it might be better to actually move the entire /home folder onto another partition.)

---

### Post by incen on 2008-02-24
If typing
```
sudo fdisk -l
```

it shows all the partitions in my system. However, what command to know what each ID refers to? Like 83 = ext3... I saw my friend did it once but I didn't remember.

---

### Post by ByteJuggler on 2008-02-24
> **incen said:**
> If typing
```
sudo fdisk -l
```

it shows all the partitions in my system. However, what command to know what each ID refers to? Like 83 = ext3... I saw my friend did it once but I didn't remember.

Go into fdisk (e.g. "sudo fdisk /dev/sda" or whatever) and type "l" (for "list") from the fdisk prompt.

---

### Post by TheThingfish42 on 2008-02-24
Thank you very much for a quick easy solution to my problem. It is for this very reason that I have completely stopped using windows. The Ubuntu community is amazing, friendly and helpful. After 15 years of Windows I just couldn't stand it anymore. Every issue I have run into in Ubuntu I have found easy solutions for through this wonderful community of people. Thank you all once again. Ubuntu for the win! :)

---

