---
title: "Do I need to completely Reinstall Ubuntu to change my HD Partition configuration?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by tepidarium on 2007-07-29
Hi,

I would like to add more Gigabytes to my Ubuntu  partitions, both / and /home.  I downloaded GParted, but it doesn't seem like I can alter the size of the partitions the way I want to.  Basically, I want to shrink my Windows XP partition - but the way my partitions are sequentially arranged seem to make it difficult to do. They are in the following order:

1. Windows XP 87.5 Gig
2.Extended 
 - /swap3 Gig
 - /home 4 Gig
3. /  12.5 Gig
4. Notebook Installed Recovery Partition 5 Gig

If I want to grow the "/" partition to 20Gig and the /home partition to 35 Gig - it seems that because the paritions are physically out o order, this is harder to do.  Am I wrong?  I've used the Live CD of Gparted...

Do you think I need to completly reinstall Ubuntu, wipe out the /, /home, /swap partitions and reorder them so that /home and / are closest to the win xp partition?  I'd rather not do this.

Thanks for any help.

---

### Post by bigfox on 2007-07-29
You might be able to resize and move partitions while booted to the live CD with Gparted.

The Live CD has Gparted on it.

---

### Post by ugm6hr on 2007-07-29
In GParted LiveCD - have a look at the Features (I think that's what it is called) from the GParted menu (first on the left).

It lists which file systems can be shrunk, grown and moved.

The Gparted website suggests the latest version can do all of these functions with NTFS / ext2 / ext3 / linux-swap.  So you should be able to achieve what you want.  Perhaps try doing one thing at a time:
1. Shrink Windows partition -> Apply
2. Move extended partition -> Apply
3. Move linux-swap -> Apply (not sure if this will be necessary)
4. Grow extended partition and /home ->Apply
5. Grow / -> Apply

This is obviously a lot of manipulation - so make sure everything is backed up!
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

---

### Post by tepidarium on 2007-07-29
What is confusing me about Gparted  is that "Resize" and "Move" is one option "Resize/Move"  but only realy the Resize option seems to work... in the sense that you can add free space above and below the partition in question but you cannot "pick up" a parition and physically leapfrog it over  other partitions that reside next to it.  

I'm loathe to reinstall Ubuntu, particulalry because I just got my Beryl coniguration working really well... (on my Ati x1400 no less!)

---

### Post by ugm6hr on 2007-07-29
> **tepidarium said:**
> What is confusing me about Gparted  is that "Resize" and "Move" is one option "Resize/Move"  but only realy the Resize option seems to work... in the sense that you can add free space above and below the partition in question but you cannot "pick up" a parition and physically leapfrog it over  other partitions that reside next to it.

Unfortunately, Move means move the start of the partition to the left or right, but not, as you said, leapfrog over another partition.  But, as long as you keep the order the same, you can achieve your partition sizes.  It just means having to move the linux-swap as well.

---

### Post by tepidarium on 2007-07-29
> **ugm6hr said:**
> Unfortunately, Move means move the start of the partition to the left or right, but not, as you said, leapfrog over another partition.  But, as long as you keep the order the same, you can achieve your partition sizes.  It just means having to move the linux-swap as well.

Are you saying that I should lop off the 50gb from the xp partition and have it "trickle" down through the other partitions by way of increasing and decreasing the physical free space around those partitions until all of the free space is, essentially meted out in the way that I want it to be distributed?  

Any downside of doing it this way?

---

### Post by ugm6hr on 2007-07-29
> **tepidarium said:**
> Are you saying that I should lop off the 50gb from the xp partition and have it "trickle" down through the other partitions by way of increasing and decreasing the physical free space around those partitions until all of the free space is, essentially meted out in the way that I want it to be distributed?  

Any downside of doing it this way?

Yes.  Downside = multiple moves / shrinks / grows, so greater risk of data loss.  Hence my previous comment.

---

### Post by buixuanduong1983 on 2007-07-29
Normally I have this partition configuration:
1. / Ubuntu 10G
2. Extended
- swap 1G
- data 24G
- backup (ghost, hidden) 5G

For me Windows is no more needed, I can do anything I want with Ubuntu. I backup (monthly) my data by CDROM, so now it is very easy for me to re-install all, even delete all partition and do a fresh install.

to tepidarium: I would resize Windows partition, create a dummy partition, use Ubuntu Live CD to backup all data there, then rearrange all your partition as you like, then re-install all OS.

---

