---
title: "My partition is misbehaving!"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by H3retic on 2008-01-13
When I installed ubuntu, I gave it 17 gigs to play with, out of a 200 gig hd.  The rest is divided in win XP partitions.  Not surprisingly, when I started using ubuntu to download videos more often, it filled up, and now I have only 300 megabytes of data left.

How do I take space from my windows partitions, and transfer them to my linux partition?  I know Gparted was made for this.  I tried using the parted magic live cd, which uses Gparted without mounting  the linux swap drive line the 7.10 live cd, but it doesn't allow me to reallocate data the way I want to.  Something about me having more than four main partitions, but why would that matter since I'm not creating a new partition.

Now I have 50 unallocated gigabytes of data that I want transferred.  How do I graft it unto the main linux partition?

---

### Post by autocrosser on 2008-01-13
What you most likely want is a separate /home partition.There ia a very good guide in Tutorials & Tips to help you.
Lots of info here:  [http://ubuntuforums.org/showthread.php?t=656138](http://ubuntuforums.org/showthread.php?t=656138)

---

### Post by Kilz on 2008-01-13
> **H3retic said:**
> When I installed ubuntu, I gave it 17 gigs to play with, out of a 200 gig hd.  The rest is divided in win XP partitions.  Not surprisingly, when I started using ubuntu to download videos more often, it filled up, and now I have only 300 megabytes of data left.

How do I take space from my windows partitions, and transfer them to my linux partition?  I know Gparted was made for this.  I tried using the parted magic live cd, which uses Gparted without mounting  the linux swap drive line the 7.10 live cd, but it doesn't allow me to reallocate data the way I want to.  Something about me having more than four main partitions, but why would that matter since I'm not creating a new partition.

Now I have 50 unallocated gigabytes of data that I want transferred.  How do I graft it unto the main linux partition?

Yes, you may have problems with that cd, for me it always messed things up. But it will let you create a partition. Once you have it created and formated ext2 or 3 you can create a folder. I made a files folcer inside my home folder. Then use /etc/fstab to auto mount the partition as that folder.

---

### Post by H3retic on 2008-01-13
> **autocrosser said:**
> What you most likely want is a separate /home partition.There ia a very good guide in Tutorials & Tips to help you.

If I could add more space to such a partition, then yes I suppose.  How would I work towards that?

---

### Post by autocrosser on 2008-01-13
What I'm saying is create another partition & follow the steps to change it to your /home.

---

