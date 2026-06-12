---
title: "Using an Addonics IDE Flash HDD"
date: 2007-06-30
forum: Apple PPC Users
---

### Post by Biz_reporter on 2007-06-30
I've been reading on Lowendmac.com about replacing Powerbook HDDs with solid state memory via an Addonics IDE flash adapter.  However, none of the Lowendmac articles address running Ubuntu or any other version of Linux with these "drives."  I see no reason why it wouldn't work.  However, before I invest money in the project, I wanted to know if  anyone here tried it?  If so, did it improve performance?  How did it impact battery life?  

Links:
[http://lowendmac.com/reviews/07/flash.html](http://lowendmac.com/reviews/07/flash.html)
[http://www.addonics.com/products/flash_memory_reader/ad44midecf.asp](http://www.addonics.com/products/flash_memory_reader/ad44midecf.asp)

---

### Post by ssam on 2007-07-01
the interface of compactflash is electrically identical to an ide hard disk. the only difference is the physical size.
[http://en.wikipedia.org/wiki/CompactFlash](http://en.wikipedia.org/wiki/CompactFlash)

i use a cheap cf to fullsize ide adaptor to have one of my computers (a via epia) boot from a CF card. i did not have to do anything special to make it work (appart from a very light install so it would fit in 1gb).

it has been running for over a year without any trouble. it is formatted is ext2, there are other filesystems that take into account how flash memory degrades, but it would be more work to get ubuntu to use those. having a swap partition on flash memory might cause to much ware. my system has enough RAM that it does not need a swap partition.

I think it would be wise to have in your mind that the CF card may ware out in just a few years, but by then the price will have dropped by a large factor.

don't expect massive improvements in performance. access time is a lot better, but throughput is slower than harddisk. somethings will get faster, some will get slower.

a final thing is that old computers have limits on how much disk space they can see.

---

### Post by Biz_reporter on 2007-07-01
So in other words, you've done it with x86 Ubuntu.  I'm guessing then it shouldn't be a problem with the PowerBook.  As for memory degradation, I'm not too worried, considering I'm primarily intending to use the old computer as a simple portable Web browser for around the house, so most files will be stored on other computers.  Thanks for the info.  If I get around to the project, I'll report back how well it went.

---

