---
title: "Partitioning on a RAID0 install"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by kamil212 on 2006-06-12
Hi all,
My setup:
AMD64 3200+ on ASUS K8SE Deluxe or somthing
1GB of DDR400 (2 512s)
GeForce5900XT (128MB, 256bit)
2 160GB SATA on VIA SATA RAID onboard controller (I'm guessing fakeRAID, right?)

I was looking to find the simplest installation of Ubuntu only system (no winXP) on my RAID0 array.
(I know the risks of RAID0, so thanks to all that are going to warn me about it)
I found the walkthrough:
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")
and [https://wiki.ubuntu.com/FakeRaidHowto]("https://wiki.ubuntu.com/FakeRaidHowto")
but I get lost after the formating part. Is there a simple install for us n00bs?

Also, what are the recommended simplest partitions for my setup? 
boot partition??? (500MB???); root(/)???; swap(2GBs); home(remaining)
I know what swap is but am kind of shady on all of the rest (I have kind of an idea but not sure)

And, partition types? I see 'ext3' everywhere, should I just stick with that?

Thanks a lot in advance,
-Kamil

---

### Post by kamil212 on 2006-06-12
Any help would be greatly appriciated.

---

### Post by kamil212 on 2006-06-12
If I'm not doing any multibooting, am right to assume that I don't need the boot partition, just the 2GB swap and the rest root?

---

### Post by loney on 2006-06-23
The guide at [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto) is the simplest fakeraid install I've seen. Booting from RAID0 has been a challenge in the past. I don't recommend it for most folks, although it may be easier in Dapper. I suggest disabling the BIOS raid and doing the basic install with the following partitions:

/dev/sda1 / 159G
/dev/sda2 swap 1G
/dev/sdb1 /home 159G
/dev/sdb2 swap 1G

(same size and priority swap at end of each drive)

Check back in a couple of years and Ubuntu may have a transparent fakeraid install. I hear gentoo has this now.

---

