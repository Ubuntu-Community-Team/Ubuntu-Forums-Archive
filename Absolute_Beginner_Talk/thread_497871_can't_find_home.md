---
title: "can't find /home"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-10
Hi.

I've just made a new /home partition for all my documents, but now when i boot up in ubuntu, i cant find it. Is there a command or something that i need to do to mount it ?

---

### Post by czepluch on 2007-07-10
I really need help on this one.

---

### Post by black_ice on 2007-07-10
from the terminal 

#cd /

#ls 


write up these commands and post the result

---

### Post by czepluch on 2007-07-10
> **black_ice said:**
> from the terminal 

#cd /

#ls 


write up these commands and post the result

Nothing happens when i write them

---

### Post by black_ice on 2007-07-10
how please make sure 

cd / that command will put u at the top of /

then ls will make listing of that please make sure you wrote it in right syntax

---

### Post by czepluch on 2007-07-10
> **czepluch said:**
> Nothing happens when i write them

I can acces one of my /home drives, but i've made another one from some free space i took from my windows partition, so that i had a place to put my documents, so now i've got two /home drives, but i can only find the one that has been there the whole time. Is there a way that i can find the other drive?

---

### Post by black_ice on 2007-07-10
try to find it at /root/home

---

### Post by czepluch on 2007-07-10
> **black_ice said:**
> try to find it at /root/home

Cant find it :(

---

### Post by black_ice on 2007-07-10
i think that you cannot make file that named with any item of the file system ,, and i think that ur new /home is not created at all ,, any how try to make new one under your default /home and named it wil docs or any thing 

hope to be helpful as i can

---

### Post by czepluch on 2007-07-10
> **black_ice said:**
> i think that you cannot make file that named with any item of the file system ,, and i think that ur new /home is not created at all ,, any how try to make new one under your default /home and named it wil docs or any thing 

hope to be helpful as i can

Hmm. Don't really understand. I've made the partition with the boot CD and then you want me to change it to what ?

---

### Post by wormser on 2007-07-10
It sounds like you created a new folder called home on another partition.  I am not sure if having two home folders will cause a problem.   You need to mount this new partition with the home folder.  Where did you create it? /dev/hda?/?  Then it needs to be mounted with the mount command.  Once that is working then you can permanently add it to the /etc/fstab file.

---

### Post by black_ice on 2007-07-10
mmm ,,  are you sure that your now /home is created ? .

or where did you create it ? .

---

### Post by FleetAdmiral74 on 2007-07-10
In adminstration - Gnome Partition Editor, is there a /home partition?

If not, what do you get if you fire up terminal and just type in "ls" without quotes and hit enter?

---

### Post by czepluch on 2007-07-10
> **black_ice said:**
> mmm ,,  are you sure that your now /home is created ? .

or where did you create it ? .

I just created it as a /home partition - for storing documents.

Really don't know what to do, and it is stupid just to have so much unuseable space.

---

### Post by stepan2 on 2007-07-10
first we have to know what drive it is . do fdisk -l in root , and go to hte partion table you put  the home partion on .  It is probably either sda or hda . In there are names like sda1 , or hda1 and they tell you how much space they have find the one that matches your new created home partion (say sda4) . Then i nterminal as root , type mount /dev/sda4 . then your home partion will be mounted

---

### Post by czepluch on 2007-07-10
> **stepan2 said:**
> first we have to know what drive it is . do fdisk -l in root , and go to hte partion table you put  the home partion on .  It is probably either sda or hda . In there are names like sda1 , or hda1 and they tell you how much space they have find the one that matches your new created home partion (say sda4) . Then i nterminal as root , type mount /dev/sda4 . then your home partion will be mounted

What do you exactly mean by doing something in root?

---

### Post by wormser on 2007-07-10
> **czepluch said:**
> I just created it as a /home partition - for storing documents.

Really don't know what to do, and it is stupid just to have so much unuseable space.

We need to find the location of this partition.  This should be an easy way.

```
sudo gparted
```

Now find the location of this new home partition.  It will be something like /dev/hda5.  Post the results.  Then we will mount the partition.  My only concern is that this is just a new folder called home and it might interfere with the /home.  You might want to call it something else.  Or you will have to copy your /home/users to the new home folder and change /etc/fstab to point to the new home folder then reboot.  That might hose your system if not done right, so I recommend just calling it storage and creating folders for each user in it.

---

### Post by FleetAdmiral74 on 2007-07-10
I think he means put "sudo" without quotes before the command, so something like 

```
sudo command-here
```

---

### Post by czepluch on 2007-07-10
> **stepan2 said:**
> first we have to know what drive it is . do fdisk -l in root , and go to hte partion table you put  the home partion on .  It is probably either sda or hda . In there are names like sda1 , or hda1 and they tell you how much space they have find the one that matches your new created home partion (say sda4) . Then i nterminal as root , type mount /dev/sda4 . then your home partion will be mounted

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3076416   12  Compaq diagnostics
/dev/sda2   *         384        1721    10747485    7  HPFS/NTFS
/dev/sda3            2934        7296    35045797+   f  W95 Ext'd (LBA)
/dev/sda5            2934        5730    22466871    7  HPFS/NTFS
/dev/sda6            6504        7111     4883728+  83  Linux
/dev/sda7            7112        7296     1485981   82  Linux swap / Solaris
/dev/sda8            5731        6503     6209091   83  Linux

that is what comes when i type: sudo fdisk-l

---

### Post by wormser on 2007-07-10
> **czepluch said:**
> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3076416   12  Compaq diagnostics
/dev/sda2   *         384        1721    10747485    7  HPFS/NTFS
/dev/sda3            2934        7296    35045797+   f  W95 Ext'd (LBA)
/dev/sda5            2934        5730    22466871    7  HPFS/NTFS
/dev/sda6            6504        7111     4883728+  83  Linux
/dev/sda7            7112        7296     1485981   82  Linux swap / Solaris
/dev/sda8            5731        6503     6209091   83  Linux

that is what comes when i type: sudo fdisk-l

Do you know which drive in the list is the new home one?  Then we can mount it.
 
```
mount /dev/sda8
```

I am guessing that it is sda8.  There might be some other options needed in the mount command.  I am not an expert with mount.

---

### Post by stchman on 2007-07-10
> **czepluch said:**
> Hi.

I've just made a new /home partition for all my documents, but now when i boot up in ubuntu, i cant find it. Is there a command or something that i need to do to mount it ?

Try typing

```

cd ~

```

then type

```

pwd

```

This will tell you where your /home directory is.

---

