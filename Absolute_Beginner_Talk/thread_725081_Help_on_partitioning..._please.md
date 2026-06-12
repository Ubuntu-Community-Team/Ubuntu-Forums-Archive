---
title: "Help on partitioning... please"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-15
I have a 750GB SATA hd that I want to install Ubuntu on...

I think I want the following partitions:
1)  /   root of 20GB (this is where OS/system files go)
2) swap of 2gb (I have 1GB of RAM)
3) /home  730ish GB for home folders

Unclear on a few options... Which is the boot turned on?  the root?
Depending on the type, some as where you want the partition placed, beginning or end?  Does this make a difference?
What do each go under:  options of logical or primary    ?

---

### Post by glennric on 2008-03-15
Don't make your / partition so big.  I made my root partition about 12 gigs and I only use 7.5 of those.    That is more than most people use.  I have a lot installed and the full linux kernel source on that partition.  For the swap partition you probably only need about a gig, although it never hurts to have more swap if space isn't an issue.  The boot directory will be put on the / partition.  Make all of the paritions primary.  It doesn't really matter what order you put the partitions in.

---

### Post by banewman on 2008-03-15
> I have a 750GB SATA hd that I want to install Ubuntu on...

I think I want the following partitions:
1) / root of 20GB (this is where OS/system files go)
2) swap of 2gb (I have 1GB of RAM)
3) /home 730ish GB for home folders

Unclear on a few options... Which is the boot turned on? the root?
Depending on the type, some as where you want the partition placed, beginning or end? Does this make a difference?
What do each go under: options of logical or primary ?

Boot will be in /
Beginning is best - for speed
the boot partition should be primary - the others are you're choice - works ok either way
:)

---

### Post by bsharp on 2008-03-15
There really isn't a need for a 2G swap partition, unless you really want it.  

On the part where it boots from, it depends where you install GRUB.  If you install it to the MBR (the default), then it will boot from the MBR and then GRUB will point to your /root partition, I believe.  Someone correct me if I'm wrong.

---

### Post by Diabolis on 2008-03-15
"/" is where your root folder will be, so thats where ubuntu will be installed.

Primary partitions are partitions that can be booted from, and you are limited to 4 primary partitions. When you run out of primary partitions and you still need more bootable partitions, then you make logical partitions. In that way you can have for example 2 logical partitions with 3 primary partitions in each one so you get a total of 6 primary partitions.

Where to place your partitions depends on which is their purpose. It doesn't really matter unless you want to resize them in the future. For example you make 3 partitions: sda1 with 20gb, sda2 with 500gb and sda3 with 20gb. One option would be to place them like this:

```
sda1 with 20gb, sda2 with 500gb and sda3 with 20gb.
```

The problem with that order is that if in the future you want to increase sda1's capacity, you won't be able of doing it unless you shrink sda2. 
Also, you can't just delete sda1 and sda3 and make a new 40gb partition, you would have to juggle around with sda2.


My recommendation is to place the partitions that are more likely to change together and on the end of your hard drive.

---

### Post by BlizzofOZ on 2008-03-15
How do you make different sda s?

I don't see that in Ubuntu's setup...

---

### Post by glennric on 2008-03-15
The sda's that he is referring to are the linux device names of the partitions.  He means create partitions with those sizes.  Linux will take care of making those device names.  

Note to Diabolis:  Change your terminology when speaking with newbies.  There is no need to speak of sda's and such when you are talking about partitioning.  Not at this point at least.

---

### Post by BlizzofOZ on 2008-03-15
thank you... I saw sda when I was attempting to partition, but didn't see that it had created different sda names.

Thanks to all who answered!!!

---

