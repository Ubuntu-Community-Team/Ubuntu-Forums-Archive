---
title: "Reinstallation problem v7.04 - specifically with partition management"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by wobwill on 2007-08-22
Hi All, 

Thanks in advance for your help.

I am installing Ubuntu for the third time now (for a variety of reasons - the last being that I totally lost /home after trying to move it to a separate partition). 

I have run the live CD and have got to the point of partitioning the hard disk and have chosen to do this manually. I have set three partitions: swap, /, and /home, expecting that this will lead to a situation where the OS is on the / partition and /home is on the /home partition. When I click next I am told that I need to reformat the / partition.

My questions are 

1) is my assumption that creating a /home partition while installing automatically lead to having the /home directory on that partition correct? If not how do I achieve this?

2) How do I set the partition manager to reformat the hard disk so that the partitions I have described can be created? (That is if the answer to question 1 is a simple 'yes')

Will.

---

### Post by milton1 on 2007-08-22
> **wobwill said:**
> 
1) is my assumption that creating a /home partition while installing automatically lead to having the /home directory on that partition correct? If not how do I achieve this?

As long as you tell the installer to mount /home on that partition, yes.
> 

2) How do I set the partition manager to reformat the hard disk so that the partitions I have described can be created? (That is if the answer to question 1 is a simple 'yes')

Will.

Confused; it sounds like you have already selected a manual partition with the layout you desire. The installer should take it from there. Let it run the format; see what happens.

---

### Post by forestpixie on 2007-08-22
if it wants you to format the partition tick the box next to the partition

in future once you've got a seperate /home, during the install you wouldn't format that home partition thus keeping you're data safe on /home

---

### Post by wobwill on 2007-08-22
Thank you both for getting back to me.

I've ticked the (painfully obvious!) boxes telling the partition manager to format the partitions. 

How do I ensure that the installer will mount the /home directory on the /home partition?

The intaller page looks a little like this:

/dev/sda
  /dev/sda1 swap
  /dev/sda2 ext3 /
  /dev/sda3 ext3 /home

following each line with 'sda' in are the size of the partition and the amount of space used. When setting up the /home partition in the partition manager in the box labelled 'mount point' I typed in '/home'.  

Before I go onto the next stage, is what I have done so far enough to ensure that the /home directory will be mounted on a separate partition to the rest of the OS?

Will

---

### Post by forestpixie on 2007-08-22
yep - that's exactly how I did it

---

