---
title: "Partition Ubuntu Drive for Windows XP"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by oakbz on 2007-09-25
For starters, here is the spec's of my hard drives.

120gig drive -- Windows XP OS -- Full
500gig drive -- Ubuntu OS -- Partitioned into 160gigs (Ubuntu) and 340gigs (free space)

I would like to know if its possible to take the 340gigs free space on the Ubuntu (500gig) drive and make it read/writeable by windows and NOT Ubuntu?

Currently windows does _not_ recognize the 500gig drive, but Ubuntu _does_ recognize the 120gig drive.

Thanks

---

### Post by logos34 on 2007-09-25
use gparted to format the free space as NTFS.  As long as you don't place an entry in fstab, it won't mount in linux and thus you won't be able to read it--ubuntu won't even know it's there.

So the 500 gb drive is not visible at all in windows (control panel>computer mgmt>disk mgmt)? The partition containing ubuntu should show up, if only as 'unknown' type.  (you need the fs-driver if you want read+write access to ext3 in windows).

---

### Post by oakbz on 2007-09-25
ok, I'm a newb to Ubuntu, I dont know what gparted and fstab are.

Yes, now that I went to disk mgmt I see the drive, and it says the 340gigs is "Unallocated" and the 160gigs is "Healthy (uknown partition)"

Again, sort of a newb but I dont know what the fs-driver and ext3 are.

---

### Post by logos34 on 2007-09-25
[B]alt+F2

gksudo gparted[/B]

click on unallocated space and create new NTFS partition

ext3 is the filesystem type of your ubuntu partition

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by oakbz on 2007-09-25
so do i download the fs-driver on my windows OS or Ubuntu?

---

### Post by mysticmatrix on 2007-09-25
> **oakbz said:**
> ok, I'm a newb to Ubuntu, I dont know what gparted and fstab are.

Yes, now that I went to disk mgmt I see the drive, and it says the 340gigs is "Unallocated" and the 160gigs is "Healthy (uknown partition)"

Again, sort of a newb but I dont know what the fs-driver and ext3 are.

Hmnn. Well few day ago in some other thread you replied me that you can't see 2nd disk in disk management.

Anyways, try this

1) In Windows, open disk management.
2) Right click the unallocated space, and choose Format
3) Assign a appropriate letter to new partition

Now. check if things are working by transferring few files. When done, reboot to Ubuntu and post output of this command
```

cat /etc/fstab
```

---

### Post by oakbz on 2007-09-25
if i format that won't it lose ubuntu? or will it just format that part of the partition?

---

### Post by oakbz on 2007-09-25
when I go to partition it says "primary" or "extended" partition...which do I want to use?

---

### Post by mysticmatrix on 2007-09-25
> **oakbz said:**
> also, formatting isnt an option when i right click the unallocated free space...just new partition and properties.  should I partition the whole thing and then format?

Use create a new partition and format it.
If you want you can create multiple partitions.

---

### Post by oakbz on 2007-09-25
primary or extended partition?

---

### Post by Sef on 2007-09-25
> when I go to partition it says "primary" or "extended" partition...which do I want to us

XP needs to be on the first primary partition.

---

### Post by crazybilly on 2007-09-25
just be careful that you only select the unused space (and not the ubuntu partition) and you should be fine.  And yeah, just click 'new partition'.  I ASSUME it'll ask you to format....I can't remember.

on a related note, gparted is a partitioning utility for linux (it's a lot like Partition Magic only freer).  I just checked and it's not installed on my machine (feisty), so you might need to install it via synaptic or apt-get.

I'd do it that way, b/c:

1. gparted is handy to have around
2.  I trust gparted more than I trust windows, when it comes to partitioning

fs-driver is the Windows driver that will let windows read your ubuntu partition.  Which is handy when you realize you saved some little file you really need on your Ubuntu desktop, rather than in My Documents.

In any case, you should be fine. Just be careful, pay attention and double-check yourself.

---

### Post by mysticmatrix on 2007-09-25
> **oakbz said:**
> primary or extended partition?

any one, but extended would be just better.
BTW, you can create 3 primary partitions and just any number of extended partitions.

PS: I'll go for lunch, will return in half an hour.

---

### Post by oakbz on 2007-09-25
hmm...I created the new partition in Windows and it didn't ask me to format.  It now says "Extended Partition, Free Space" -- I right clicked and it still didn't have an option to format.  Also, I checked "My Computer" to see if it showed up there and there was nothing.  Any idea's?

---

### Post by oakbz on 2007-09-25
Nevermind.  I deleted that partition and made it a primary instead.  It now functions properly in windows :) thanks guys!!

---

