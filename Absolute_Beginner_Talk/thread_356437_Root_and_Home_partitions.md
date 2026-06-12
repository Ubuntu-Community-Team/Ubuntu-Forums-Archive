---
title: "Root and Home partitions"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Pai on 2007-02-08
I've viewed these forums for a while, but this happens to be my first post; Hello, and thank you all in advance.

So I'm currently running XP, but today I was planning to reformat my drive and install Dapper (not dual-booting).  

My question however, is about partitioning my drive for the best setup.
Before I go on, here are some system specs in case they are needed: 3.0 GHz Pentium 4 || 2.0 GB Ram || 256 MB GForce 6800, with the current partitions: 
[img]http://img70.imageshack.us/img70/9145/partitionsoi0.png[/img]
I'm not sure what the 3.85 gb and the 39 mb partitions are, but I plan on leaving them both.  I know that one of them is the system recovery tool included when I purchased my Dell, which is used to boot to rather than a CD when reformatting. 

I believe I need a **/** (root), /home, and swap partition. The first two should both be ext3, right? And is there anything else I need?

Assuming the above statement is correct, my next question is about the size of each.  I've heard many different things about how big to make the swap, root, and home partitions, so I'm really not sure what is correct.  I would ideally like to switch/upgrade between different distros without losing all my files (or having to manually store them elsewhere).  Can I do this?

Summary: How big do I need to make the swap, root, and home partitions?

Any other last minute advice is appreciated.

Miscellaneous info: I will basically be using this setup to browse the internet, program (nothing more than Java and Python), playing media (music and videos) and just general tinkering to gain experience.

---

### Post by jblebrun on 2007-02-08
On my machines, the majority of space is allocated to my /home partition. I have about 20 gigs for the root partition, which has always been more than enough. If you install tons and tons and tons of software, you may find otherwise, but it's unlikely. 

The recommend swap size is 2-3 times your system's memory.

Finally, put everything that's left over on the /home partition. 

You can switch between distros without losing your /home partition, in most cases. There are some caveats, and you may have to manually move some configuration directories to new places, but I've moved home directories without too much of a problem. 

If you do any manual configuration in /etc or anywhere else outside of /home, you'll need to back it up and manually replace files in the new distro. Different distros keep things in different places. Some distros have drastically differing ways of managing certain service configurations, so keep that in mind. If you're not planning on doing much service configuration, it's a moot point.

Note that web pages and databases are often stored in /var by default (part of the / partition).

---

### Post by Lord Darth Vader on 2007-02-08
You will need at least 3 Gb partition for "/". It is up to you to have "/home" partition or not. Therefore the size is related to how much data you might want to save in that partition. You may decide not to have any partition for /home, in that case that folder will be created in you / (root) partition and obviously 3 Gb for root would not be enough. I say 5 Gb is a good bet. 
For swap partition you may size it according to your physical memory. In your case, swap can be equal to your memory size.

---

### Post by Medieval_Creations on 2007-02-08
I've been playing with Linux for years now & it's funny to see how everyone has their own way of setting up their PC's.  You really only **need** 2 partitions / & swap  :)  The sizes of those partitions is up to you really, but this would be my suggestion.

```
15GB - /
20GB - /home
1GB - swap
3GB - /var
remainder - /mnt/Storage_Ext3

```

But that's just me.

---

### Post by Lord Darth Vader on 2007-02-08
My setup is like:

/ -->  20 GB
/home -->  42 GB
swap --> 512 Mb (my ram is 512 and swap is usually left unused)

But I didn't know we need a partition for /var.
What is the benefit?

---

### Post by Medieval_Creations on 2007-02-08
> **Lord Darth Vader said:**
> 
But I didn't know we need a partition for /var.
What is the benefit?

You don't really need a var.  But all the log files are typically stored there, and I have had issues in the past with publicly accessed PC where I've had log files over loading a drive virtually making the system unusable since the / partitions is full.

So I've gotten into the habit of using it.

Really you only need 2 partitions / & swap.

---

### Post by jingo811 on 2007-02-08
> The recommend swap size is 2-3 times your system's memory.
I've read that theory usually applies when you have (RAM below) <1 Gb.  Once you hit the (1 Gb RAM) mark or beyond you only need to multiply by 1.  So in your case 2 Gb swap would if I'm correct be even too much swapping space.  If I were you I'd make that 1 Gb Swap even if you have 2 Gb RAM.  (Less noise from your Harddrive, more work for your silent RAM)

If I'm not mistaken
/ = space for your Ubuntu and future programs you install + updates.
/home = space for your work files, mp3 + avi (some installed programs gets in here though)

---

### Post by Pai on 2007-02-08
> **Medieval_Creations said:**
> You don't really need a var.  But all the log files are typically stored there, and I have had issues in the past with publicly accessed PC where I've had log files over loading a drive virtually making the system unusable since the / partitions is full.

So I've gotten into the habit of using it.

Really you only need 2 partitions / & swap.

So it's probably not necessary for a beginning user to create a /var partition?

Also, could you expand on the */mnt/Storage_Ext3*?  What is this mount partition? This is the first time I've heard somebody recommend it. 

Thanks.

---

### Post by schorsch on 2007-02-08
> **jingo811 said:**
> I've read that theory usually applies when you have (RAM below) <1 Gb.  Once you hit the (1 Gb RAM) mark or beyond you only need to multiply by 1.  So in your case 2 Gb swap would if I'm correct be even too much swapping space.  If I were you I'd make that 1 Gb Swap even if you have 2 Gb RAM.  (Less noise from your Harddrive, more work for your silent RAM)

If I'm not mistaken
/ = space for your Ubuntu and future programs you install + updates.
/home = space for your work files, mp3 + avi (some installed programs gets in here though)

I your swap device is smaller than your amount of RAM you will not be able to use the hibernate mode. This is not so important if you use a desktop, but if you use a laptop hibernating could be desired ....

---

### Post by Medieval_Creations on 2007-02-08
[QUOTE=Pai]So it's probably not necessary for a beginning user to create a /var partition?
[/quote]

Probably not needed of a normal user.  Just become a force of habit for me.

*Also just an F.Y.I.: if you plan on doing any web development in Ubuntu, Apache2 puts the www folder in /var.*

> 
Also, could you expand on the */mnt/Storage_Ext3*?  What is this mount partition? This is the first time I've heard somebody recommend it. 


This is basically just a storage Partition.  I don't like having all my files under 1 partition.  I've learned from multiple Winblows crashes that if the OS takes a dive your S.O.L. usually. By breaking up your HD into more partitions your OS can crash and you can reinstall with minimal data loss.  Example: I can reload any flavor of Linux on my desktop and because all my pics, movies & whatever else I want is safe on it's own partition.

I call it Storage_Ext3 because when I was dual-booting with Ubuntu & XP I had to storage partitions 1 for Linux & the other for XP, hence the naming convention; Storage_Ext3 for Linux & Storage_NTFS for XP.  I put them under /mnt for 2 reasons; 1, I started out with Slackware linux and that's where typically you would mount things & 2, if you put them under /mnt instead of /media in Ubuntu it won't show up on your desktop.

```
Here is how I have my Desktop setup partition wise (w/ 4 HDs):
1 x 40GB (hda)
     hda1 - 15GB - /
     hda2 - 20GB - /home
     hda3 - 2GB - swap
     hda4 - 3GB - /var
1 x 160GB (hdb)
     hdb1 - 60GB - /mnt/VirtualBox
     hdb2 - 100GB - /mnt/Storage_Ext3
2 x 200GB (sda1 & sdb1 - Raid0)
     /dev/md0 - 400GB - /mnt/Mp3s

```

---

### Post by jblebrun on 2007-02-08
Some people have said you only *need* 2 partitions and swap... that's not true. You only need one partition, the root partition. I've run a number of systems that just use one giant partition, and never ran into any problems.

---

### Post by Medieval_Creations on 2007-02-08
> **jblebrun said:**
> Some people have said you only *need* 2 partitions and swap... that's not true. You only need one partition, the root partition. I've run a number of systems that just use one giant partition, and never ran into any problems.

jblebrun is right.  You only must have 1 partition.  Most due setup a 2nd as a swap.  As with most things it just comes down to personal prefrance.

---

