---
title: "Software RAID (RAID 0 Add to Array)"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-06
Ok so I installed my ubuntu server and created a raid zero array for my home dir. I a computer that I dont need anymore of got a 250 GB hard drive.

Is it possible to add that hard drive to my raid 0 array without losing the data that is already on there?

If so how would I go about it?

---

### Post by guysmiley25 on 2006-10-27
Anyone?

---

### Post by guysmiley25 on 2006-11-05
Bump

---

### Post by nyinge on 2006-11-09
> **guysmiley25 said:**
> Ok so I installed my ubuntu server and created a raid zero array for my home dir. I a computer that I dont need anymore of got a 250 GB hard drive.

Is it possible to add that hard drive to my raid 0 array without losing the data that is already on there?

If so how would I go about it?

I'm a little confused here.  You said that you've already created a raid 0 system, in which I believe there are 2 hardrives involved.  Now, you want to add an another disk to your already set up raid 0.  So, that'd make it 3 drives in total.  To my understanding, RAID 0 consists of only 2 hardrives.  Unless you change the RAID type, I'm not sure how you'd add an extra drive to it.

Maybe, you might want to create an LVM, but adding another drive to an existing RAID 0 is beyond my knowledge.  :mrgreen:

---

### Post by guysmiley25 on 2006-12-04
Oh I see. So I cannot have a RAID 0 Array with more than 2 drives. Is LVM the only way I can get done what I want?

---

### Post by tokkosta on 2006-12-11
Well ofcourse you can add a third hard-drive to a raid0 setting but i belive you will loose the data. Not sure though.

---

### Post by psusi on 2006-12-12
I believe that newer versions of mdadm and the kernel can dynamically reshape the array to add a third drive.  Otherwise, backup your data, reformat, and restore.

---

### Post by guysmiley25 on 2007-04-19
How would I go about doing this?

---

### Post by Nzer24 on 2007-10-04
To backup you would have to get some sort of external drive or a few DVDs... depending on the size.

After you backup, now you need to repartition. There must be a partition on the new disk that is EXACTLY the same size as each of the other disks in the array, otherwise you will lose capacity. If there is extra space you can just format that for something else. Now just put all of the drives into a new software RAID 0 configuration and it should work.

P.S. I'm thinking about making an RAID 0 array myself, but I need it to work on both windows XP and Ubuntu (both on a separate disk from the array). A. how did you do this one, and B. Do you think it will work in my case?

---

### Post by psusi on 2007-10-07
The only way you are going to get a workign raid0 that both windows and linux can see is with a hardware fakeraid.  See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).  

As for the OP, man mdadm.  You can use it to add a new disk and reshape the array I am fairly certain, without data loss.

---

