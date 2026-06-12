---
title: "Problem with Gparted and PartedMagic"
date: 2007-11-19
forum: Apple Intel Users
---

### Post by Eatrice on 2007-11-19
I just finish installed Ubuntu Gutsy, and everything works great :)

My problem now is that I set my ubuntu partition to small at the start. I would like to shrink the HFS+ partition and enlarge the ext3 partition. 

I tried to use Gparted from LiveCD to shrink the HFS+ partition, but i was just hang there and did nothing. so I stop it after 5 mins (I saw that the completion % = 0%).

So now I am scare that does Gparted able to shrink HFS+ partition without data lost. Should I try it again and just wait for it longer.

 I also looked at parted magic, but my English is not so good, so I dont know that can it shrink HFS+ partition without datalost

---

### Post by ericartman on 2007-11-19
Last time I used gparted I was knocking down 100 gig of a partition. From a 300 gig to a 200 gig partition and it took about 8 hours. Yeah its long and slow but I've used it about 5 times resizing and formatting partitions and its never missed yet. Setting it all up and going to bed if the easiest to me.

Cart

---

### Post by cyberdork33 on 2007-11-19
> **Eatrice said:**
> I just finish installed Ubuntu Gutsy, and everything works great :)

My problem now is that I set my ubuntu partition to small at the start. I would like to shrink the HFS+ partition and enlarge the ext3 partition. 

I tried to use Gparted from LiveCD to shrink the HFS+ partition, but i was just hang there and did nothing. so I stop it after 5 mins (I saw that the completion % = 0%).

So now I am scare that does Gparted able to shrink HFS+ partition without data lost. Should I try it again and just wait for it longer.

 I also looked at parted magic, but my English is not so good, so I dont know that can it shrink HFS+ partition without datalost
partedmagic is just a modified version of gparted. either will do the same thing.

---

### Post by Eatrice on 2007-11-20
Thanks! I will give it a shot again tonite.

Just like some opinions

After I shrink the HFS+ partiton, and I would like to share the free space between the 2 OS, should I foramt it as HSF+ or FAT.

And My orginal partition looks like this in a single HD
1st partition - FAT (rEFIt)
2nd partition - HFS+
3rd partition - ext3
4th Partition - swap

If I change the partition to this:
1st partition - FAT (rEFIt)
2nd partition - HFS+
3rd partition - FAT/HFS+ (Share data)
4th partition - ext3
5th Partition - swap
Will rEFIt see my ubuntu partition and boot? I scare that I moved the partition and wont boot again?

---

### Post by Grey Box on 2007-11-21
With the Macbook you can't have more than four (4) partitions. If you want to share something then dump your swap partition and format that as FAT32. Have a [ swap file set up in your main partition]("https://help.ubuntu.com/community/MacBook") if you want to have swap space. 

Just a side note: When I instaled Ubuntu, I needed rEFIt to correct the partition table before I could boot. The Ubuntu Installer warned that there was some inconsistency with the partition table, but I chose 'ignore' and it all worked out. I installed Ubuntu over an older Windows installation which I'd set up using Bootcamp. (They make you think Bootcamp is the bee's knees and that you can't do without it. What a load of rubbish!)

---

### Post by cyberdork33 on 2007-11-21
> **Grey Box said:**
> With the Macbook you can't have more than four (4) partitions. If you want to share something then dump your swap partition and format that as FAT32. Have a [ swap file set up in your main partition]("https://help.ubuntu.com/community/MacBook") if you want to have swap space.

While there is a 4 partition limit that windows can see, you can definitely have more than 4 partitions on your disk and it will work fine. Make swap partition #5 (or even OSX itself) and then make your shared partition one of the first 4.

Bootcamp is definitely not needed as you are using it for is partitioning the hard drive which can be done other ways.

---

### Post by Eatrice on 2007-11-21
> **cyberdork33 said:**
> While there is a 4 partition limit that windows can see, you can definitely have more than 4 partitions on your disk and it will work fine. Make swap partition #5 (or even OSX itself) and then make your shared partition one of the first 4.

Bootcamp is definitely not needed as you are using it for is partitioning the hard drive which can be done other ways.

oh thanks

So I just need to put the first 4 partition that OSX need to see, so I can put swap in the 5th partition that OSX dont need it.

Thanks again, I learn something today :)

---

### Post by cyberdork33 on 2007-11-21
> **Eatrice said:**
> oh thanks

So I just need to put the first 4 partition that OSX need to see, so I can put swap in the 5th partition that OSX dont need it.

Thanks again, I learn something today :)
Actually OSX can see any partition too, it is the EFI emulated MBR that is limited to 4 partitions (and windows)

---

