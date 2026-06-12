---
title: "How will 7.04 work with installing on RAID arrays?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by hobs0n on 2007-04-20
I have 2 Raptors in RAID 0 on my comp and I wonder how hard it is to get Ubuntu 7.04 to install and boot  with that? I made a [thread](http://ubuntuforums.org/showthread.php?t=382575) about this before and Kakalaky made a phat *** guide for me how to get it to work but that was waaaaay to much work for a Lonux newb like me ;) So thats why Im making a thread again. And if this has been asked many times and already answered I apologize. Im a tired as hell and too lazy to search for this for 7.04 right now ;)

The RAID is on the software fake RAID system that comes with the Nforce 4 chipset.

---

### Post by tbg58 on 2007-04-21
The only advice I would give you is to avoid using RAID0.  You get a single volume with the aggregate size of both your drives, but because your data is striped across both drives, if you lose either drive you lose ALL of your data -- I don't think you want that. 
Unfortunately once its set up you don't have any way of breaking the RAID set on a RAID0 setup non-destructively.
Please consider backing up your data, reformatting the drives either without RAID or using RAID 1, which mirrors your data.  

If you use no RAID, you will have the same capacity you have now, but with two file systems.  Reads and writes will be a bit slower because for any one file you will only have one spindle swinging.
RAID0 is fast on writes because you are writing the same amount of data through two spindles, but a single failure on either drive loses all your data.
RAID1 will be slower on writes because the controller has to write all the data twice -- once on each drive, but your data is redundant -- if either drive fails, you still keep all your data, but you will have only the capacity of one drive.

This doesn't answer the question you asked, but I am really sincere in asking you to consider not using RAID0 except if you just want fast performance and aren't worried about losing all your data.

Good luck!
- Rob

---

### Post by hobs0n on 2007-04-21
> **tbg58 said:**
> The only advice I would give you is to avoid using RAID0.  You get a single volume with the aggregate size of both your drives, but because your data is striped across both drives, if you lose either drive you lose ALL of your data -- I don't think you want that. 
Unfortunately once its set up you don't have any way of breaking the RAID set on a RAID0 setup non-destructively.
Please consider backing up your data, reformatting the drives either without RAID or using RAID 1, which mirrors your data.  

If you use no RAID, you will have the same capacity you have now, but with two file systems.  Reads and writes will be a bit slower because for any one file you will only have one spindle swinging.
RAID0 is fast on writes because you are writing the same amount of data through two spindles, but a single failure on either drive loses all your data.
RAID1 will be slower on writes because the controller has to write all the data twice -- once on each drive, but your data is redundant -- if either drive fails, you still keep all your data, but you will have only the capacity of one drive.

This doesn't answer the question you asked, but I am really sincere in asking you to consider not using RAID0 except if you just want fast performance and aren't worried about losing all your data.

Good luck!
- Rob

Thanx for giving me info but I already know how RAID 0 /1 /5 /6 works. I only  have the OS and games on this computer, everything else is on the server :)

---

### Post by NewbieNik on 2007-04-21
tbg58 has missed the point of RAID0. The benefit of access speed to the RAID is substantial. Backups can be done to any other drive at your leisure!
Anyhow, I set-up my two 320Gb Sata' through the alternate install CD and avoided the "fake" Nv4 RAID as I found it unstable in Windows.
Ensure you partition the drives the same (I set 5Gb for Swap, 50Gb for root and 265Gb for data) on each drive. When partitioning set each partition as RAID, not Ext file format.
Once both drives are parted, congiure the RAID (top selection in that menu) and make sure yo pair them up correctly, 1 to 1, 2 to 2, etc, etc, then you can set each of the RAID partitions for their usage (Above example gave 10Gb which I set to Swap, 100Gb which I set as EXT3 for / and 530Gb which I set manual as /data)
All is as standard from there on in....
I have to say to develpors, Canonical and all involved that Feisty is a gorgeous, simple, quick and perfect example of a desktop OS. Pay heed MS, this is how an OS should be!!!

---

### Post by hobs0n on 2007-04-22
Well I have Windows on my RAID0 array now so Ubuntu much support the N4RAID from the install ISO but I might buy a seperate HDD to install Ubuntu on :)

---

