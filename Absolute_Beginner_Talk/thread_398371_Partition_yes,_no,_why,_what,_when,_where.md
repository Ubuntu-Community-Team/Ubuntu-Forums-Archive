---
title: "Partition: yes, no, why, what, when, where"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by jve901 on 2007-03-31
Hi. I've never tried Ubuntu or Linux before & I've read until I got cross-eyed here. I'd like to install Ubuntu on the same drive as XP. I have a copy of Partition Magic. I've never partitioned a drive before. I have an image of Ubuntu 6.10. I have plenty of space so I'd like to dedicate 5GB to Ubuntu.

Do I need to partition to install Ubuntu? I know now the answer is Yes.
Should I partition before doing anything with Ubuntu? (Partition Magic in XP)
Should I then format this partition as Linux?
Or will the Ubuntu image I have, partition the drive upon installation?
Will either way of partitioning allow me to select what area of the drive to partition? (So I don't lose data)
When I'm ready to install Ubuntu using the live CD (CD image), can I decide where on the drive to slap this thing?
Will the partition be clearly visible?

The documentation is very confusing. I believe if we were given a choice of different avenues to follow in order to install this thing, depending on our PC's configuration, this forum wouldn't be so lengthy. I've even read the Read This First part of the forum, the illustrated guide to installing Ubuntu, and partitioning is still unclear.

Thanks for any help.

---

### Post by mikewhatever on 2007-03-31
A lot of new information is usually confusing, so you should not be surprised.
To create Ubuntu partitions, you need unallocated disk space, which is the space not allocated to any of the existing partitions. If there is no such space, which is often the case, you'll need to resize one of the existing partitions. Resizing will make unallocated space in which you'll need to create Ubuntu partitions(root,swap), format them, and then install. Presumably, it is described and pictured in the documentation. Ubuntu desktop installer has a partitioning tool, you do not need another one.

---

### Post by aysiu on 2007-03-31
1. Don't install Ubuntu just yet. Use the Desktop CD (also known as the "live CD") for a couple of weeks. Get used to it first. Make sure you really want it.

2. Do **not** use Partition Magic to do partitioning. It's unnecessary, as Ubuntu's installer comes with a partitioning program, and I've heard about people encountering problems installing Ubuntu after using Partition Magic.

3. Understand a bit about partitioning and partitioning schemes before doing anything. Read this page:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

4. **Always back up everything important to you before setting up a dual-boot**
If you know what you're doing and don't back up, there's a 99% chance everything will work out okay.
If you don't know what you're doing and don't back up, there's a 60% chance everything will work out okay.
Whether you know what you're doing or not and you do back up, there's a 100% chance everything will work out okay.

5. Two dual boot guides that will help you out:
**Desktop CD** - [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
**Alternate CD** - [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by jve901 on 2007-04-01
Thanks for the help!

You say to try Ubuntu by using the Live CD for a couple of weeks, however it is so extremely slow, it takes forever just to open Firefox. Unfortunately I don't think this is an option.

Thanks for the links, they're very helpful & the illustrated guide is easy to follow. On step 6 of 7 of the installation process, is that slider to determine how much space to allocate to Ubuntu or to WinXP? I'm planning on taking the first selection "Resize IDE1..." as this seems like a good choice for a beginner.

I'm planning on using 5GB out of 40 on my laptop. I currently have 25GB free... I'm planning on creating a simple NTFS + Linux partition setup. If for any reason Ubuntu doesn't work out for me, can I uninstall it & kill the partition easily?

Thanks again!

---

### Post by dracomordag on 2007-04-01
if as of right now you just have a standard XP-installed drive, i'd plan it as follows

Partition 1 (your current NTFS partition (WinXP)): size it as small as possible, probably with a spare 5 GB just in case you still need a couple of apps in XP (if not, maybe you can wipe it!)

Partition 2: your "/" (root) folder. format it as Ext3, i'd say 10 GB or so.

Partition 3: your "/home" folder. again, ext3 format. this is where the majority of your Ubuntu is gonna go, so make it big. It essentially holds all of your data except some background settings, system-run ish, etc.

if youre installing with Feisty (you should be... there's really no need to install Edgy now if you're starting fresh), the included gParted program will walk you through all of this very easily.

---

### Post by rstevesat on 2007-04-02
Hi Everybody,
                     I have got a VISTA preinstalled on my laptop . Now i used the VISTA partionig tool to partition 145 GB with keeping 40GB for Ubuntu. Now it shows 105GB as NTFS and 40GB as unallocated . Is this OK? Now if i want to install Ubuntu , i can use a live CD . Install on the unallocated space. Will it show up? If it shows then i install Ubuntu and then use the partitioner in Ubuntu to do the partition for swap and main data. Am i correct till here ?

---

### Post by dptxp on 2007-04-02
Go ahead and install. Select about 8 GB for '/' (root), 2 GB for SWAP and rest for data after selecting 'Manual Partitioning' in step 5 (i think 5). If you want Windows also to access the data,
format the data part in FAT32, else choose EXT3.

Make sure that the new partitions show in next step, ensure that you do not format the Windows partition, and proceed.

Install in 30 minutes flat.

---

### Post by johnny4north on 2007-04-02
i would ghost your current xp setup 1st.  thanks Ubuntu

---

