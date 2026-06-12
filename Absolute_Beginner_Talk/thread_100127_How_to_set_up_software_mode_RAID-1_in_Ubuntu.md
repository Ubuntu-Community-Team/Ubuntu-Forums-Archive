---
title: "How to set up software mode RAID-1 in Ubuntu?"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by Mateo1041 on 2005-12-06
Hi everyone,

I just finished installing Ubuntu 5.10 server edition and installed KDE.  I have two 36.4 GB hard-drives.  The first of these is the only one I used.  I'd like to use the second for RAID.

I've searched high and low, but haven't found anything that is helpful to me that clearly explains how to set up RAID for someone who hasn't done it before.

I looked at the following document:

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.1](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.1)

But can't figure out how to download raidtools2.  It keeps giving me "Package raidtools2 has no installation candidate" errors.

I also looked here:

[https://wiki.ubuntu.com/Installation/RAID1?highlight=%28RAID%29](https://wiki.ubuntu.com/Installation/RAID1?highlight=%28RAID%29)

But the article doesn't fully explain how the partitions should be laid out prior to typing the commands it mentions.  Can this be followed from the command line once Ubuntu is fully installed?

I also looked here:

[https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28RAID%29](https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28RAID%29)

But that didn't seem too user friendly.

Argh!  Here is approximately how my first 36.4 GB hard-drive is set up so far:

> /boot, primary, ext3, 250 MB
/, logical, ext3, 5 GB
swap, logical, swap, 1.5 GB
/var, logical, ext3, 1.5 GB
/home, logical, ext3, 28 GB

Does anyone have any ideas?  Isn't RAID fairly standard on a server?  I'm surprised there is not more information out there that is user friendly.  :-(

Any help would be appreciated.  Thanks.

- Matt.

---

