---
title: "View Linux Partitons from Windows?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Penzao on 2006-09-06
Hey i just was able to figure out how to view my windows partitonas and files from Ubuntu. But now i cant seem to find out how to view my linux partiton form windows! All my searches have come up empty, any help would be appreciated :D

---

### Post by Chickencha on 2006-09-06
Assuming your Linux file system is ext2 or ext3, check out [http://www.fs-driver.org/](http://www.fs-driver.org/) and download the Windows utility there.  It'll let you read and write to your Linux partitions and it works really well.  (If you don't know what your Linux file system is, then it's probably ext3.  If it's something besides ext2 or ext3, I don't know how to help you.)

---

### Post by Omnios on 2006-09-06
Hi I used to have my Linux drives mounted in windows but from what I read win has no idea pertaining to ownership or privaledges so I decided I did not want my Linux core files excessable in windows. 

 ANyone else have any more info on this. Id hate to get a win virus currupting my main Linux partition.

---

### Post by msandersen on 2006-09-07
> **Omnios said:**
> Hi I used to have my Linux drives mounted in windows but from what I read win has no idea pertaining to ownership or privaledges so I decided I did not want my Linux core files excessable in windows. 

 Anyone else have any more info on this. Id hate to get a win virus currupting my main Linux partition.
The [ext2 IFS driver]("http://www.fs-driver.org/") currently doesn't recognise Linux permissions. But unless you specifically mount a partition, a virus or anything else can't touch the data, so one lesson is to never mount your Root partition in Windows and only mount Data partitions. And to practice safe computing by wearing a condom on your head. No, wait... Got that last part wrong. A modem with a router, a good firewall, automatic updates and some common sense goes a long way. Setting a good password for your Windows account helps too.
I'm not too worried about viruses on Windows; when I've got one, it's due to my own carelessness opening unsafe files (though Norton gave it the all-clear).

---

