---
title: "Feisty partition question"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by trents on 2007-04-21
I'm not a complete noob to Linux but there are a lot of gaps in my knowledge.

Been trying to do an install of Feisty using my existing Edgy partitions which are two in number: /dev/sda3 ext3 of about 26 gb in size and /dev/sda4 swap of about 750 gb in size. I guess Feisty doesn't use Gparted as the  partitioning tool anymore and when it comes to setting up the partitions it wants me to establish a "root partition of at least 2 gb" and to "specify a mount point".  It puts a check in the box by the ext3 partition but won't let me put a check in the box next to the existing swap partition and it won't let me go any farther. Do I need to allocate space for a root partition from one of the existing partitions, either the NTFS one or the ext3 one? I'm confused because none of this was a problem when upgrading from Dapper to Edgy.

Thanks, Steve

---

### Post by raja on 2007-04-21
The root partition is your main partition. This will be /dev/sda3 on your system. Select that and mount it a '/'. The swap partition will be recognised by its filesystem (swap). While you are at this, you may also consider creating a separate /home partition by shrinking the root partition and creating a new partition in that space.

---

### Post by trents on 2007-04-21
Is there an advantage in establishing a seperate home partition?

---

### Post by raja on 2007-04-21
Well, if you reinstall and want to retain the data and settings you have in your /home partition, you can choose not to format it and only format the root partition. It is better, in my opinion.

---

### Post by trents on 2007-04-21
Thanks. That makes sense. By the way, raja, the problem with the partiioning I was having turned out to be that I wasn't mounting ext3 at \. 

Another question. What is all this in Feisty install about migrating documents and settings? Where would this migrate the accounts to? Feisty? I don't want the Feisty install to mess up my Windows partitions or its settings so that I can't boot into Windows or so that I loose my documents and settings in Windows? Do I need to check those account boxes to prevent this? I'm not sure what the migration tool is asking me to do or what it accomplishes.

Thanks, Steve

---

### Post by raja on 2007-04-21
What the migration tools is supposed to do is to take the bookmarks, addressbook, IM settings etc and have them ready in Ubuntu when you need them. Dont worry about your windows settings getting messed up. Ubuntu cannot even write to your NTFS partitions at the moment. I would suggest you try to use the migration tool.

---

### Post by trents on 2007-04-21
Does it take them from the existing Ubuntu accounts or from the Windows accounts? I only see Windows accounts in the Migration too window.

One more question: What would be an appropriate size for a /Home partition if I were to create one?

Thanks, Steve

---

### Post by raja on 2007-04-21
Sorry I misunderstood your question. It will take the settings from your existing windows account, not the Ubuntu one.

---

### Post by raja on 2007-04-21
> **trents said:**
> 
One more question: What would be an appropriate size for a /Home partition if I were to create one?


Depends on what you want to put there. In my case, I have all my data on another separate partition. I would say about 1-2GB for settings and all + whatever space you need to keep data should do. You can see how much space you have used on your current Ubuntu installation. ```
df -h /home
```

---

### Post by trents on 2007-04-21
Thanks. Okay, I'm resizing ext3 from 27 gb to 17 gb and making the 10 gb slice to be the home partition. Does that sound reasonable?

Steve

---

### Post by trents on 2007-04-21
But wait, the partitioning tool tells me the new 10 gb slice is "unsusable". How do I establish a partition in that space?

---

### Post by raja on 2007-04-21
You can even get the root partition down to 10 GB. Its fine otherwise.

---

### Post by trents on 2007-04-21
But what about the 10 gb of "unusable" space. It won't let me create a new partition with that.

Steve

---

### Post by raja on 2007-04-21
Is it unusable or unused? If you shrink an existing partition and create free space, you should be able to create a new partition in that space. I am not sure what your error is exactly.

---

### Post by trents on 2007-04-21
It is unusable. I'm not sure what is going on there. I think I liked gparted better.

Steve

---

### Post by trents on 2007-04-21
Finally had to delete the exising linux partitions altogether using gnome partition editor and installing Fiesty in the unallocated space that created. Part of the problem was I was trying to add a primary home partition when there were already four of them (XP, Vista, linux root and linux swap), which is the max when you are sharing the drive with NTFS, I guess. Now I know I could have designated the home partition as logical (extended?) instead of primary and I would have been ok. By  the time I figured all this out that (after some research) I had managed somehow to screw up the linux root partition so that the Feisty partitioner wouldn't work with it so I just delete my linux partitions with Gnome partition editor (g-parted?) and installed in the newly created unallocated space. I still don't like the new partitioner in Feisty.

I notice that Feisty created 3 partitions, one of which is an extended partition. Wonder what that is for.

---

