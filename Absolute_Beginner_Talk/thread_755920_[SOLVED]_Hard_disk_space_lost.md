---
title: "[SOLVED] Hard disk space lost???"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by GoCool on 2008-04-15
I used to have WinXP and now I loaded Ubuntu (Gutsy) on it.

Just recently I observed that my Hard disk is showing only 75 GB, but it was a 200 GB Hard disk.



Any idea why it happened? 
And what I should do to reclaim it?

:confused:

---

### Post by aeiah on 2008-04-15
what does it look like when you view it in gparted? either the space is unallocated, or there is a partition that isnt mounted i guess

---

### Post by GoCool on 2008-04-15
> **aeiah said:**
> what does it look like when you view it in gparted? either the space is unallocated, or there is a partition that isnt mounted i guess

Sorry for asking but I never used gparted, do I need to install it separately?
How do I use it?

---

### Post by ace007 on 2008-04-15
in terminal:

```

sudo apt-get install gparted

```

It should appear under System>Admin>Partion Editor or called Gparted.  It will visually represent the space on your disk for you.  It also allows you to move/resize the partitions.

---

### Post by Paqman on 2008-04-15
> **GoCool said:**
> 
Just recently I observed that my Hard disk is showing only 75 GB, but it was a 200 GB Hard disk.


Is it a 200GB disk, or a 200GB partition?

During installation of Ubuntu you would have partitioned your drive. Each partition shows up as a separate drive to Ubuntu. Windows won't be able to see Ubuntu's partition, so will only show it's own one (C:\ drive)

---

### Post by GoCool on 2008-04-15
> **Paqman said:**
> Is it a 200GB disk, or a 200GB partition?

During installation of Ubuntu you would have partitioned your drive. Each partition shows up as a separate drive to Ubuntu. Windows won't be able to see Ubuntu's partition, so will only show it's own one (C:\ drive)

It's a 200 GB disk.
And I don't have  Windows any more.

---

### Post by GoCool on 2008-04-15
> **ace007 said:**
> in terminal:

```

sudo apt-get install gparted

```

It should appear under System>Admin>Partion Editor or called Gparted.  It will visually represent the space on your disk for you.  It also allows you to move/resize the partitions.

I'll try it.

---

### Post by Paqman on 2008-04-15
> **GoCool said:**
> I'll try it.

You won't be able to make changes to your drive though, because it's mounted. Luckily the LiveCD has Gparted on it by default, so you'll be able to just boot from that and make any changes you need to. Your drive isn't mounted when you're running from the LiveCD.

---

### Post by GoCool on 2008-04-17
I used gparted from live CD. This is the info I got

> Partition   File System       Size     Used     Unused
------------------------------------------------------------------------
/dev/sda1    ntfs               108        63         45
/dev/sda2    ext3                78         36         42


What would be the implication if I deleted the ntfs partition. I don't need the data, but will my Ubuntu boot normally after the change? (After removing the live CD from the drive?)

---

### Post by bumanie on 2008-04-17
If you remove the nfts and leave it as unallocated and don't alter the position of partitions, you should not have to do anything. However if you want to extend the partition so that ubuntu can use the whole drive, you will have to reinstall grub via the live cd as ubuntu will have effectively moved grub from (hd0,1) to (hd0,0). You would probably be best to also edit /boot/grub/menu.lst to get rid of the windows entry there too. (I think the above is correct - never tried it)

---

### Post by Tatty on 2008-04-17
Your ntfs partition will be your windows drive.  Make sure you dont want it before you delete it.

---

