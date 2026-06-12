---
title: "Physical Memory 4G, but system monitor shows only 3G"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by seantshen on 2007-06-16
I just bought a Dell with 4G memory with Ubunto preinstalled.  I confirmed via BIOS setup that the memory is physically at 4G.  But when I go into Ubunto system monitor (System-->Administration-->System Monitor), I only saw 3G. Any reasons?  How do I fully utilize the 4G i have on the box?

---

### Post by drowner on 2007-06-16
Do you have a swap partition?

---

### Post by seantshen on 2007-06-16
How do I check? Its been a long while since I did any UNIX....very rusty

---

### Post by drowner on 2007-06-16
Post the output of 

sudo fdisk -l

---

### Post by seantshen on 2007-06-16
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6         267     2104515    b  W95 FAT32
/dev/sda3   *         268         292      200812+  83  Linux
/dev/sda4             293       38913   310223182+   f  W95 Ext'd (LBA)
/dev/sda5             293         772     3855568+  82  Linux swap / Solaris
/dev/sda6             773       38913   306367551   83  Linux
seantshen@dell:~$ 



thanks

---

### Post by drowner on 2007-06-16
Ok, i'm going to hand over the someone else here.

I remember something about someone having Swap with 4gig of ram, but the ram appearing smaller because a 32bit system can't do more than 4gig.

is this true? Am I making things up?

---

### Post by icechen1 on 2007-06-16
> **drowner said:**
> Ok, i'm going to hand over the someone else here.

I remember something about someone having Swap with 4gig of ram, but the ram appearing smaller because a 32bit system can't do more than 4gig.

is this true? Am I making things up?
that is true.

---

### Post by seantshen on 2007-06-16
But this is 4G.  If 32 bit system cannot handle more than 4G, at least it should be able to handle 4G, right?

---

### Post by Vague on 2007-06-16
> **seantshen said:**
> But this is 4G.  If 32 bit system cannot handle more than 4G, at least it should be able to handle 4G, right?

No.  Anything more than 3GB isn't going to be usable on a 32-bit OS.  For a more eloquent (and technical) explanation than I could give, take a look at this: [http://www.dansdata.com/askdan00015.htm](http://www.dansdata.com/askdan00015.htm)

---

### Post by mahiyar on 2007-06-17
I read the whole article and from what I understand nobody should be allowed to sell memory greater than 3 gig, I am surprised that of all the vendors dell is handing out this stuff. Will have to be careful in the future.

---

