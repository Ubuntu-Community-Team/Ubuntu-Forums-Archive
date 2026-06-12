---
title: "Does anybody Know how to install  Gutsy on a Mac (Dual Boot)?"
date: 2007-12-31
forum: Apple Intel Users
---

### Post by Jammy4041 on 2007-12-31
Hello, and  Thankyou in advance.

I am creating a guide to installing Ubuntu, and the problem is, i have not really used a Mac. I do not even own one.

So while I am OK in doing it with Windows/Ubuntu Dual boot, even complete Ubuntu hard drive, I can't help those whom will want to apply my guide to there mac. 

So can anybody help me with this, e.g. how did you install ubuntu on your mac?

Like I said, thanks in advance

---

### Post by alpinesatan on 2007-12-31
its quite an undertaking to get it all working, with airport, the isight camera, bluetooth etc.
I started from scratch, booted the os x dvd used the disk utility to partition my disk before i continued to install os x.
When done i downloaded and install rEFIt then rebooted making sure the ubuntu cd was in the drive. Chose to boot from cd. At this stage i was running the live cd.
Opened partition manager or whatever its called, formatted the second half of my HDD as ext3.
installed by clicking the nice little install icon on the desktop, chose to install to the newly formatted partition and thats it. (well very rought anyway)
As for installing the other bits there is no definitive guide. But please feel free to look at my post;
[http://ubuntuforums.org/showthread.php?p=4036966&posted=1#post4036966](http://ubuntuforums.org/showthread.php?p=4036966&posted=1#post4036966)

Kind Regards

---

### Post by russbuss on 2007-12-31
I actually just did this yesterday on my MacBook Pro C2D (not Santa Rosa) and updated the MacBook Pro wiki.  I did essentially what alpinesatan did:

1) Partitioned my HD with BootCamp.  I used the BootCamp beta for this.  If you just set your system clock to before September 31st, 2007 you can still use BootCamp beta.  I don't know how much longer this workaround will last, but I found out about it from an Apple support page.
2) Installed rEFIT on the OS X partition.
3) Booted from 7.10 Live CD (64 bit)
4) Started installation and did manual partitioning
5) Deleted the partition created by BootCamp (/dev/sda3)
6) Made a new parition 2GB smaller than the original /dev/sda3 partition (to save for swap space) and formatted as ext3.
7) Formatted the remaining free space as swap.

This worked perfectly for me.  There are additional tweaks you need to do after the install to get wireless, trackpad, etc. working properly, but these are all outlined in the wikis here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

and here:

[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

Hope this helps.

---

