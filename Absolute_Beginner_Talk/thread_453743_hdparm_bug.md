---
title: "hdparm bug????"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by coderK on 2007-05-24
Hi I just typed:
```
man hdparm
```
It displayed the discription. But on going to Terminal->Reset, it said
```
Reformatting hdparm(8), please wait.
```
I immediately closed the terminal But it managed to erase my D: drive mounted as softwares in the root. What the **** happened????
I lost all 5 GB of my data!!!!!!!!!!!!

---

### Post by Happy_Man on 2007-05-24
It's not a bug, it's a feature! :razz:

But seriously, take a break, buddy. You're stressing a bit, and making mistakes. It must be the middle of the night in India.... go to sleep.

---

### Post by coderK on 2007-05-24
Yeah it is nearly 4. **BUT I LOST 5 GB OF DATA - AND MY WINDOWS WONT BOOT. **How can you ask me to stop stressing out? And what kind of a feature reformats your hard drive when you don't want it to????

---

### Post by Terl on 2007-05-24
Are you sure it is gone?  Try the ```
sudo fdisk -l
``` again and see the output.  I really think you need to calm down and take it easy.  I know you are upset but it is too easy to make a mistake.

If you really typed man hdparm it just pulled up the manual page.  The follow on reformatting hdparm8 refers to it reformatting the manual page.  The  8 means it is in section 8.

Read what hdparm does:  [hdparm man page]("http://www.die.net/doc/linux/man/man8/hdparm.8.html")

---

### Post by coderK on 2007-05-24
How does that command help?
Anyways, the Output is:
```
kush@k-Ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8296    66637588+   7  HPFS/NTFS
/dev/sda2            9732       19456    78116062+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            8297        9601    10482412+  83  Linux
/dev/sda4            9602        9731     1044225   82  Linux swap / Solaris
/dev/sda5            9733       16845    57135172+   7  HPFS/NTFS
/dev/sda6           16846       19456    20972826   83  Linux

Partition table entries are not in disk order
kush@k-Ubuntu:~$ 
```
In Gparted - there is a screenshot down here, both NTFS partitions have warnings but C: drive warning in properties says "Unable to find mountpoint"
D: drive says:
"Unable to read the contents of this filesystem!
Because of this some operations may be unavilable.

Did you install the correct plugin for this filesystem?"


And I also gave a screenshot of disk usage analyzer. D: drive is mounted as softwares and C: as windows. Doesn't look good.

---

### Post by Terl on 2007-05-24
I have a feeling you are going to have to reinstall windows.  The ntfs sections show no usage (look at your linux block, it has a partial yellow fill).  That is not a clean partition arrangement at all.  It looks like you shrunk windows by splitting it when you partitioned.  If so that is why windows is so messed up.  

Originally you said you had the windows in two partitions.  How did you partition it?  I am thinking you took something like this: -----------------------|------------------------ and shortened the first half toward the left and the second half toward the right.  Like this -------------|new linux home and such here|---------rest of windows-----------|

If so, I am unsure how to recover this especially when you said you do not have the xp disc right now.

Thank you for posting the pictures, they helped.

---

### Post by coderK on 2007-05-24
So my data really is gone right? Because I can access the Windows partition but in softwares (the partition which was D:) is empty. And I partitioned the C: drive to the left and the D: drive also to the left? Have I done something wrong? and what about the los of data? how did that occur since you say it just formats the manual???

---

### Post by Terl on 2007-05-24
> **coderK said:**
> So my data really is gone right? Because I can access the Windows partition but in softwares (the partition which was D:) is empty. And I partitioned the C: drive to the left and the D: drive also to the left? Have I done something wrong? and what about the los of data? how did that occur since you say it just formats the manual???

Any loss of data could have occurred during the partitioning.  the 'man hdparm' command did not reformat your drive.  Partitioning is not always perfect.  Before you partition windows portions you should always defrag them.  Windows freaks out rather easily and it can be hard to correct it - especially without the rescue disc.

You could try going to bootdisc.com and see if they have a windows xp rescue disc for download.  

Did you happen to install ntfs3g on your system?  If not get ntfs3g and ntfs-config through synaptic.  Then try and run the config (it will be in applications->system tools).  Maybe you can mount the drives and have a look.

---

### Post by Happy_Man on 2007-05-24
Yeah, I'll agree with terl.... it looks more and more like you need to reinstall... especially looking at that partition table..... sorry if I seem mean, but the truth hurts sometimes....

---

### Post by Terl on 2007-05-24
> **Happy_Man said:**
> Yeah, I'll agree with terl.... it looks more and more like you need to reinstall... especially looking at that partition table..... sorry if I seem mean, but the truth hurts sometimes....

coderK, Happy_Man despite his name may have bad news but I too think you need to reinstall.  I know it is painful but we all have to do it sometime.  I, like many others on this forum, have messed up stuff before and had to do the same.  It sucks but it is also how we learn.  :(

Sometimes we just have to bite that bullet, put in the install cd, and start over.  Always remember too, back-up, back-up and back-up!  If you have anything necessary on Ubuntu now, I would copy it to a cd or pen drive now.

coderK:  I will check for the next couple hours.  Try getting the ntfs3g like I said.  Maybe, just maybe, we can save some of your windows files.  Do you have a way to save them?

---

### Post by psusi on 2007-05-24
Yes, the man hdparm has nothing to do with anything here.  The question is, how did your partitions look originally, what did you do to them in gparted, and what is wrong with them now?

When you say your windows won't boot, what specifically do you mean?

---

### Post by coderK on 2007-05-25
Its okay, data is fine I had a friend help me fix it. The drives were not mounted: I gave the details here if you need to refer to anything. Thanks again guys. Now I just have to reinstall Windows.
Here is the other thread:
[http://ubuntuforums.org/showthread.php?t=453399](http://ubuntuforums.org/showthread.php?t=453399)

---

