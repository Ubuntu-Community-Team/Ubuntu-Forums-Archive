---
title: "Need help with partitions"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by MillTech on 2008-04-07
Hi, I'm new to Ubuntu and am configuring a new server, The server has 4 500GB drives and I need some assistance with how best to set the system up. All the server will be doing is running a mySQL database.

My thoughts were to setup a RAID1 pair of partitions for the / partition. A RAID5 for the swap area but then I'm unsure what other folders should be setup on their own partitions, presumably with RAID5.

Primarily I would like the bulk of the storage for the mySQL database storage.

Can anyone assist please?

---

### Post by tamoneya on 2008-04-07
There is no need for you to have the swap in a raid 5 partition.  What I would do is setup RAID 10 with all 4 drives.  This would result in 1 TB worth of usable space and would also be rather quick.  From there I would go about making my swap partition and OS partitions as necessary.  

Making a RAID 1 out of two drives and then making RAID 5 out of the additional two drives make no sense.  RAID 5 on two drives would be a BIG waste since you would only get 1 drive worth of storage and you wouldnt get any speed boost and you would have a processor load when writing since it has to calculate the parity bits.

---

### Post by MillTech on 2008-04-07
I started off with the idea of using RAID10 but I can't find how to do this with the partition settings in Ubuntu. Also will GRUB work from a RAID10 system?

---

### Post by tamoneya on 2008-04-07
i believe it is possible but not fun by anymeans.  I would make RAID 10 and then run the OS from a small harddrive that I found lying around.  If you dont have any lying around you can just get like 80GB since it is about the smallest you will find.  Then I would mount the RAID 10 to wherever you are storing your mySQL database.

---

### Post by pseudo-random on 2008-04-07
I'm guessing this is for work right?
Does your employer approve of Ubuntu / Does it meet MIL-STD requirements?
Just curious. Great news if it does though. Bad news for Microsoft's profits though...:)

---

### Post by MillTech on 2008-04-07
> **tamoneya said:**
> i believe it is possible but not fun by anymeans.  I would make RAID 10 and then run the OS from a small harddrive that I found lying around.  If you dont have any lying around you can just get like 80GB since it is about the smallest you will find.  Then I would mount the RAID 10 to wherever you are storing your mySQL database.

Yes, that is an option. I'll see what is in the junk box.

---

### Post by MillTech on 2008-04-07
> **pseudo-random said:**
> I'm guessing this is for work right?
Does your employer approve of Ubuntu / Does it meet MIL-STD requirements?
Just curious. Great news if it does though. Bad news for Microsoft's profits though...:)

Nope, its not for work.

---

### Post by keld on 2008-05-11
There is a howto on setting up a system with raid10 at [http://linux-raid.osdl.org/index.php/Preventing_against_a_failing_disk](http://linux-raid.osdl.org/index.php/Preventing_against_a_failing_disk) .
(I wrote most of it). I have used the setup with 4 disks - the main data in a /home raid10,f2 and it runs fine. I get about 320 MB/s out of it in almost idle state when I cat a 2 GB file to /dev/null, on a slightly loaded system I get about 200 MB/s out of it (just tried it).

---

### Post by MillTech on 2008-05-11
Thanks for the info, thats a big help.

---

