---
title: "Expanding a partition?"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Cloudy on 2006-08-26
So, I have a 160GB Windows partition and a 15GB Ubuntu partition. Now that I've started using Ubuntu more than Windows, I want to expand my Ubuntu partition to 30 or 40GB - but how would I go about it? Could I possibly shave about 15-20GB off my Windows partition (using System Rescue CD) and is there any way I could reallocate that free space to my Ubuntu partition?

---

### Post by 505 on 2006-08-26
I only know of Norton PartitionMagic that can resize partitions without formatting the data. It's a Windows program and you have to pay for it.

---

### Post by Paul133 on 2006-08-26
I think you can just use gparted ( [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) ) to resize the partition. Resize Windows to, say 40 gigs, and you get 20 gigs of free space. Then resize Ubuntu to 35 gigs!

---

### Post by Cloudy on 2006-08-26
System Rescue CD allows you to resize a partition without formatting the data, I'm fairly certain of it - when I installed Ubuntu on this PC it's what I used, and what I did was take 15GB off of my Windows partition..

I hope that made some semblence of sense, because it's 5:12 in the morning and I'm not thinking straight. >_>

EDIT towards Paul133: There's a KDE counterpart, right? Kparted, I think?

---

### Post by v1ct0r on 2006-08-26
Gparted of course. :)
But I use the Ubuntu Live Cd to resize partitions. 

Just :  **sudo gparted**

Another elegant solution is the [Gparted Live CD](http://gparted.sourceforge.net/livecd.php). Just burn and use. 

Have fun with that.

---

### Post by Cloudy on 2006-08-26
Thanks, everyone. :D

---

### Post by masnevets on 2006-08-26
Unfortunately if your harddrive has the windows partition before the linux partition, you will not be able to grow it. The reason is because you can only expand the end of ext3 partitions with gparted, so if you want to expand it, I suggest using an external/extra harddrive to copy the ext3 partition, then delete it on the main harddrive and recopy it in the new, bigger location.

---

### Post by Paul133 on 2006-08-26
And there's always sfdisk (which I just learned about a minute ago)!

---

### Post by Cloudy on 2006-08-26
> **masnevets said:**
> Unfortunately if your harddrive has the windows partition before the linux partition, you will not be able to grow it. The reason is because you can only expand the end of ext3 partitions with gparted, so if you want to expand it, I suggest using an external/extra harddrive to copy the ext3 partition, then delete it on the main harddrive and recopy it in the new, bigger location.

Aww.. you're sure of this?

---

### Post by Paul133 on 2006-08-26
Are you sure of that? You can't shrink the NTFS partition and grow the ext3 partition? I only have experience in the alternate partitioner, so I'm not sure.

---

### Post by masnevets on 2006-08-26
Yeah, if you load gparted and look in GParted > Filesystems, move is not available for ext3, and that's what you want. Another solution is to just delete the linux partition and reinstall if you don't have too many personal files (burn onto CD?), but I have also heard some of the proprietary Windows partition managers like partition magic and norton ghost allow the move function. I haven't checked this myself; just thought I'd throw it out there in case it's useful to you.

---

### Post by Paul133 on 2006-08-26
What do you mean "move"? Isn't mit just resizing NTFS and ext3?

---

### Post by masnevets on 2006-08-26
Move refers to moving the beginning of the partition, which is what he will want to do. Let's say it looked like this:

| ------ Windows ------ | | ----- Linux ----- |

And you want to do this:

| --- Windows --- | | ## | | ----- Linux ----- |

where the ## is unallocated space. This is fine and should work in gparted. Then I take it that you want to turn it into this:

| --- Windows --- | | -------- Linux -------- |

But then the linux partition actually starts at a new location on the disk, which is not allowed as far as I know in gparted since it's not supported. I have tried to do this before without any luck, and searching on the web says that having two harddrives is the only way to get around this.

---

### Post by Paul133 on 2006-08-26
OK. Thanks.

---

### Post by Malac on 2006-08-26
> **masnevets said:**
> Move refers to moving the beginning of the partition, which is what he will want to do. Let's say it looked like this:

| ------ Windows ------ | | ----- Linux ----- |

And you want to do this:

| --- Windows --- | | ## | | ----- Linux ----- |

where the ## is unallocated space. This is fine and should work in gparted. Then I take it that you want to turn it into this:

| --- Windows --- | | -------- Linux -------- |

But then the linux partition actually starts at a new location on the disk, which is not allowed as far as I know in gparted since it's not supported. I have tried to do this before without any luck, and searching on the web says that having two harddrives is the only way to get around this.
This does work I have just done it about three weeks ago.

You just have to use the live CD open GParted in [System->Administration->Gnome Partition Editor]
and unmount all the partitions (including /swap if that is on the drive). 
Then shrink the Windows partition.
Then REBOOT  to LIVE CD again.
Then resize the Linux partition into the un-allocated space.
Worked for me no problem. :)

---

### Post by Cloudy on 2006-08-26
I think I'm going to wind up trying what Malac suggested and hope that works out..

---

### Post by Malac on 2006-08-26
Backup everything first and defrag windows at least 3 times before you start.
Better safe than sorry. :)

---

