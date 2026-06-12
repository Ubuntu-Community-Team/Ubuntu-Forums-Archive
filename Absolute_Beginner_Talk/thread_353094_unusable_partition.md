---
title: "unusable partition"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by hungrybuddha on 2007-02-04
I am 2 days old with ubuntu. i love it.

i have a dual boot rig, and i am having trouble with some unusable space.

upon installation (edgy), i followed guides on parting 10gb for the OS, and 2gb for the swap area. when i selected the 2gb, GPart asked if I wanted it in the end or the beginning of the space. i selected at the end. after it was all said and done with gpart, ubuntu was installed.

now aside from XP being on one partion and ubuntu on another, i have a remainder of 30gb that is available, but not capable of being partitioned. i went back with both GPart and disk manager in XP, and both wont touch it. right clicking does nothing in XP. GPart tags it with "unusable space".

did my swap area selection affect this area of disk?

---

### Post by carloslosgrande on 2007-02-04
I had a similar problem before, try downloading this
[HTML]http://gparted.sourceforge.net/[/HTML]
Its a more powerful partition editor and can easily fix this difficulty by resizing.
Go slowly and carefully. Good luck and fun.

---

### Post by Moulton on 2007-02-04
The DOS-style partition table only supports 4 primary partitions.  When you added the new partitions for Ubuntu, did you use up all 4 of your primary partitions?

If you have used all 4 primary partition definitions without spanning the entire disk, the remaining space will become unusable.

The solution is to define at least one extended partition, which can then be subdivided as necessary into additional partitions.

What you should do is make the fourth partition entry (the one now defined as your Linux swap area) an extended partition that spans the entire remaining space on the drive, and then subdivide it so that a small part of it is defined as your Linux swap partition, leaving the remainder to be defined later for other purposes.

It won't be fatal if you operate without a working swap area while you fix this up.  Linux can run fine without a swap area as long as you don't try to run more applications than will fit into physical RAM.  You should define the size of your Linux swap area to be about 2 to 3 times the size of your physical RAM.

---

### Post by hungrybuddha on 2007-02-04
> **Moulton said:**
> 

What you should do is make the fourth partition entry (the one now defined as your Linux swap area) an extended partition that spans the entire remaining space on the drive, and then subdivide it so that a small part of it is defined as your Linux swap partition, leaving the remainder to be defined later for other purposes.

It won't be fatal if you operate without a working swap area while you fix this up.  Linux can run fine without a swap area as long as you don't try to run more applications than will fit into physical RAM.  You should define the size of your Linux swap area to be about 2 to 3 times the size of your physical RAM.

yes, 4 have been used. i intend to reconfigure the space as the way you mentioned. Can I do this live in ubuntu, or boot from disk?

---

### Post by hungrybuddha on 2007-02-04
Ahh well

I used gparted and booted off the cd. I erased the last primary and parted an extended partition, and recreated the swap partition. and....

edgy wont boot up. it freezez at the bootskin. thats alright, i'll just reload it, only 2nd time...

---

