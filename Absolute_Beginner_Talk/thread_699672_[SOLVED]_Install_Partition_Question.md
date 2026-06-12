---
title: "[SOLVED] Install Partition Question"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-17
I am installing Ubuntu 7.10 64-bit on my server rig (see signature), and I plan on dual booting WinXP Pro and Ubuntu...

I've already installed XP on a partition that takes up about 45gigs, and I have roughly 100gigs of unpartitioned space available for my ubuntu install...
I began the install process and I am on step 4 "the partitioner" and I am faced with the following options:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/install-partitioner.jpg[/IMG]
So which do I choose?
I assume "**Guided - use the largest continuous free space**" but I wanted to check before I F' up the install.
Thanks,
-BassKozz

---

### Post by sb12 on 2008-02-17
largest free space would be correct if you already have the unpartitioned space available

---

### Post by celticbhoy on 2008-02-17
If you use the largest space you are leaving little for window's, use the first option as it advises

---

### Post by sb12 on 2008-02-17
> **celticbhoy said:**
> If you use the largest space you are leaving little for window's, use the first option as it advises

he already has windows installed though

---

### Post by celticbhoy on 2008-02-17
What about data & program space ??

---

### Post by BassKozz on 2008-02-17
> **sb12 said:**
> largest free space would be correct if you already have the unpartitioned space available
Correct I already have unpartitioned space...
Here is a Screenshot of the partitioner if I choose manual;
[IMG]http://i4.photobucket.com/albums/y105/basskozz/install-partitioner-manual.jpg[/IMG]
and here is a screenshot from GParted:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/GParted-ss.jpg[/IMG]

> **celticbhoy said:**
> If you use the largest space you are leaving little for window's, use the first option as it advises
but windows is already alloted 45gigs (I won't be needing more then that)...
The partitioner won't take away from that 1st partition (windows partition) if I use the "largest free space" option (it will only use unpartitioned space), right?

---

### Post by sb12 on 2008-02-17
> **B/-\ssKozz said:**
> Correct I already have unpartitioned space...
Here is a Screenshot of the partitioner if I choose manual;
[IMG]http://i4.photobucket.com/albums/y105/basskozz/install-partitioner-manual.jpg[/IMG]

but windows is already alloted 45gigs (I won't be needing more then that)...
The partitioner won't take away from that 1st partition if I use the "largest free space" option, right?

correct

---

### Post by BassKozz on 2008-02-17
Ok I did that (Guided - use the largest continuous free space) and here is the summery:
```
If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #2 of SCSI1 (0,0,0) (sda) as ext3
 partition #5 of SCSI1 (0,0,0) (sda) as swap

```
Is this correct?
How come it shows creating #2 & #5, where are partitions #3 & #4?

Just want to check before I pull the trigger.

---

### Post by sb12 on 2008-02-17
> **B/-\ssKozz said:**
> Ok I did that and here is the summery:
```
If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #2 of SCSI1 (0,0,0) (sda) as ext3
 partition #5 of SCSI1 (0,0,0) (sda) as swap

```
Is this correct?
How come it shows creating #2 & #5, where are partitions #3 & #4?

Just want to check before I pull the trigger.

probably because of an extended partition, that will count as a number also even though it is basically a container

---

### Post by BassKozz on 2008-02-17
> **celticbhoy said:**
> What about data & program space ??
I am mainly going to be using Ubuntu, the XP partition is just for a failsafe fall back if needed, so I shouldn't need more then ~40gigs
> **sb12 said:**
> probably because of an extended partition, that will count as a number also even though it is basically a container
Thanks,
And how come the sizes aren't listed, meaning how much space is alloted to ext3 (#2) and how much for swap (#5)?

---

### Post by seventhc on 2008-02-17
nooooooooooooooo
go back to step 4 and choose the third option "*Guided-Use the largest continuous free space*"
Then it will be a dual boot.

---

### Post by BassKozz on 2008-02-17
> **seventhc said:**
> nooooooooooooooo
go back to step 4 and choose the third option "*Guided-Use the largest continuous free space*"
Then it will be a dual boot.
What are you talking about... that is what I used?
.
.
.
::BUMP::
> **sb12 said:**
> probably because of an extended partition, that will count as a number also even though it is basically a container
Thanks,
And how come the sizes aren't listed, meaning how much space is alloted to ext3 (#2) and how much for swap (#5)?

---

### Post by seventhc on 2008-02-17
I'm just going by your first screenshot, If you changed it fine.
I saw the pic and just posted right away before you committed to it.
Sorry though.
To be sure, your screenshot isn't showing that your using largest continuous free space. There is a specific option for that, it isn't checked off in the screenshot.

---

### Post by sabatron on 2008-02-17
I just recently paritioned my drive.  If I were you I'd do this with the unallocated space:

Use 97 GB for "/" (ext3)
and the remaining .66 GB for swap

This should allow u to continue with the partition setup

---

### Post by BassKozz on 2008-02-17
> **seventhc said:**
> I'm just going by your first screenshot, If you changed it fine.
I saw the pic and just posted right away before you committed to it.
Sorry though

np,,, maybe you could help me figure out how Ubuntu Install figures out the space allotment  for ext3 and swap?
I selected the "*Guided-Use the largest continuous free space*" option and when I got to the install summery page I get:
```
If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #2 of SCSI1 (0,0,0) (sda) as ext3
 partition #5 of SCSI1 (0,0,0) (sda) as swap
```
But it doesn't say how much space was alloted for ext3 and how much for swap, should I just assume it has figured out the best way to partition?
**p.s. I currently have 4gigs of ram installed, but plan on upgrading to 8gigs eventually, shouldn't this affect my swap space needed (for optimal performance)?**
> **sabatron said:**
> I just recently paritioned my drive.  If I were you I'd do this with the unallocated space:

Use 97 GB for "/" (ext3)
and the remaining .66 GB for swap

This should allow u to continue with the partition setup
how did you come up with that calculation? is there a rule of thumb for swap space needed?

---

### Post by sabatron on 2008-02-17
Yes, you don't really need a lot of space for swap...when I partitioned my drive I did it manually and left 1 gig for swap and put the remaining gigs into ubuntu (/) leaving about 30 extra gigs in my windows (ntfs).  but you don't need a lot of space for swap...the .66 gigs will be more than enough

---

### Post by seventhc on 2008-02-17
I personally don't like the way ubuntu chooses swap. I have 1 gig ram and if I remember correctly last time I let ubuntu do it for me it gave me way to much swap. I'm not sure how it will decide for you with 4 gig's. But I'm sure it will give more than you need, this can always be changed using gparted afer the install is complete though.
Personally I do manual partitioning these days. I have had dual boots though where ubuntu did the guided -free space and it has always worked. Just to much swap, but thats never been to big a deal to me as I havent filled up my hdd yet so I don't care to much it uses unless my space becomes limited.

---

### Post by seventhc on 2008-02-17
I used to make swap 1x or 1.5x my ram, but I think thats not so important anymore considering how much ram is available these day. You have 4 gig's of ram, your swap will most likely hardly get used. I have 1 gig,  ram and depending I still usually make it between 1-2 just out of habit. I usually decide what I want my main partitions set to, then assign the remainder to swap.

> But it doesn't say how much space was alloted for ext3 and how much for swap, should I just assume it has figured out the best way to partition?
**p.s. I currently have 4gigs of ram installed, but plan on upgrading to 8gigs eventually, shouldn't this affect my swap space needed (for optimal performance)?**
Swap is like virtual memory, so the more ram you have, the less important swap becomes. if you go from 4 to 8 gig ram, I'm not even sure if you would need swap. I'd still make one probably but it won't get used. even now on mine, I use maybe 1% of my swap

---

### Post by sabatron on 2008-02-17
Check this link out

[http://lifehacker.com/software/linux-101/learn-more-about-swap-space-330755.php]("http://lifehacker.com/software/linux-101/learn-more-about-swap-space-330755.php")

I think it will help you a great deal in learning about swap space.

---

### Post by BassKozz on 2008-02-17
Well I let Ubuntu allocate the space and here are the post install results:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/GParted-postinstall.jpg[/IMG]
Looks like Ubuntu thinks I need 4gigs of swap space...
Well I can probably work with less, I think i'll leave it as is and adjust it later if I need to free up extra space for ext3.
Thanks for the help everyone :D
-BassKozz

---

### Post by seventhc on 2008-02-17
Glad you got it :)
I wouldn't worry about the swap  for now either. If you ever run out of space then you can change it. For now, just enjoy :) :guitar:

---

