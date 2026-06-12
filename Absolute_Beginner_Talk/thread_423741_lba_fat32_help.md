---
title: "lba fat32 help"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by iceb on 2007-04-26
Hi


I have tried to install the ubuntu system on my windows xp pro sp2 pc. 
I can finally run the installer from the cd and now all I had to do was install it on my external harddisk.

But after trying to do this suddenly my whole external harddisk turned into fat32 lba and not 
fat32 normal windows format and now I cannot use the external hd in windows. 
Should I uninstall or is there sometihing I can run to make my hd readable again in windows ?
Right now there are NO problems in ubuntu and I can access my external hd in ubuntu without 
errors which I cannot do in windows....


Best Regards 
iceb

---

### Post by seshomaru samma on 2007-04-26
your post is not so clear
did you install ubuntu onto an external harddisc?
what file system did you choose for it?
if its ext3 (ubuntu's deafault flesystem)- windows will not be able to read it unless you download some drivers from[ here]("http://www.fs-driver.org/")

---

### Post by iceb on 2007-04-26
Hi There


Yes I did try to install the ubuntu on an external but when the process was 5/6 it halted and paused
without giving any errors and just showed the hour glass.

Then I turned the whole pc off. And that is maybe why it is now half installed. 
But it did not work out with the link you send me it said that I do not have any other systems 
than windows and dos. 

I still cannot access my external hd though.
Yes I chose the default file format. 

How do I get my old fileformat fat32 in windows back ? 
This is how it should be. 

External hd: 

Partition V = the partition for the ubuntu install 

Partition U = the partition that windows xp cannot read and that ubuntu can read. 

So I want it so that partition V is the only partition on the pc containing ubuntu. 
Then I want the U partition to be readable by windows.

I have 160 gb data on my partition U now which I do not want to delete or loose.


iceb

---

### Post by seshomaru samma on 2007-04-27
I think I understand
I don't know why Windows can't see your partitions

the most important question is :
Can you view your two partition from Ubuntu's Live CD?

If yes then
I suggest this:
Run Ubuntu's Live CD - copy all your important files to a safe place
Try to install Ubuntu again
Post any difficulties or errors.

If no
We will have to think about a different solution

---

### Post by iceb on 2007-04-27
Hi 


YEs I can see the external hd from ubuntu after starting it but not from the menu. Is live cd
what comes when u boot your ubuntu iso on the cd ? 

How can I with ubuntu back my files up ? 

Furthermore how can I get windows to NOT tell me the
partition is not formated do you want to format now everytime I try to access 
the partition in windows xp pro ?

In windows xp pro it is now like this. 
The external hd has TWO partitions 

partition 1 where I want to install ubuntu and
this partition CAN be seen in windows and acessed

Partition 2 where windows cannot read or write to and 
says the filesystem is in RAW format 

Should I use fixmbr to make windows able to read and write to the partition or what 
shall I do here ? 


iceb 
 




l

---

### Post by louieb on 2007-04-27
If you can boot windows don't run fixmbr or fixboot either for that matter.
Your attempt to install Ubuntu on the external drive may have messed up the partition table. But you still may be able to fix it.
But we need some information. First list  the partition table.
Boot to Ubuntu live CD
Open Applications>Accessories>Terminal and run
```
sudo fdisk -l
```
Hopefully you have internet and can copy the out put here. 
It should something like this output from my external drive .
```


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sdb2            8925       19457    84606322+  83  Linux


```
Get back with that and we will go from there.

---

### Post by iceb on 2007-05-03
Hi 


I get 

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

then what to do now ?


Best Regards 
iceb

---

