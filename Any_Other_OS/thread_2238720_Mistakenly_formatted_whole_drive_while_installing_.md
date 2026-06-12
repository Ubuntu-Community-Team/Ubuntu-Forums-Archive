---
title: "Mistakenly formatted whole drive while installing ubuntu now how can i proceed to sa"
date: 2014-08-09
forum: Any Other OS
---

### Post by jatin2 on 2014-08-09
I was using win 7 on my dell inspiron N5110 having 500 GB HDD  and 2 GB RAM, with derive C was having 50GB to100GB space(can't remember  exactly) & having OS in it. Other's Derive/Partition were D and E.  Then i thought to replace my Windows 7 by ubuntu and as a fresher for  linux environment i goes with  "Erase Disk and install ubuntu" without  thinking even a single time that it will not only erase C partition but  the whole derive. And when i continued the installation , even after 8  hours it was not completed and i suspect something went wrong and force  shut down my laptop by pressing power button. Then i checked my derive  partition table with the help of Window 7 DVD and was afraid to see  there was only one partition of 463Gb(~500GB) with "0" being shown under  "Free Space Available" column. Later on i came to know that ubuntu  formatted my whole Hard-disk and installed some of the installation file  in following unsuccessful installation attempt. Now my questions are:

1.  Even if ubuntu get partially installed in my Hard derive , it must get  installed in the somewhat same Hard derives sector/track which had  initially occupied by C partition when i was using Win 7.
 
2.  So the chances are very less that it have over written anything beyond old derive C.

3.  Let me correct if i am wrong, if i have three partition of my HDD (C,D  & E) and having XYZ operating system installed in partition C then  if i format the whole HDD and merge all partition resulting into one  single partition and then installed an ABC operating system on the same  HDD without making any partition. In this situation provided post  installation size of both operating system are exactly or approximately  Same,  does the new OS's files will get overwritten over the same  sectors/tracks of HDD which were initially occupied by ABC(old)  operating system's files or the new OS will get overwritten entirely on  different HDD's tracks/sectors in respect to tracks/sectors which were  occupied by old OS.


I am asking just to clear my worries  about mistakenly overwritting anything on old D and E partitions while  installing a fresh window 7 copy(just meant to run the recovery software) and then install the recovery  software and recover my data from those sectors of HDD which were  initially occupied by Partition D and E. Because i have to recover files  only from hard drives tracks/sectors occupied by partition D and E ,  not from C partition.

A Big Thank you for your time , as i am in big trouble.

---

### Post by coldraven on 2014-08-09
Any operation that involves formatting, re-sizing partitions or installing an additional OS is inherently dangerous, that's why we are supposed to make backup copies of important data.
If you chose "Erase disk and install Ubuntu" then that is what it will do, all your partitions will be removed and a new one created. If you want to try and recover anything then **do not use the disc any more **or you will only overwrite more stuff.
Data recovery is **complicated** and it is too late at night for me to try and explain how to do it but you could start by reading this page that gives examples of using Testdisk. 
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Most people recommend cloning the drive to an external USB drive and attempt to recover files from it. That way if you mess it up your original drive is still intact and you can try again.
If you are not experienced in using data recovery tools I would suggest that you pay someone to do it for you. 
The pain you will get when you see the bill will turn you into a backup evangelist!

---

### Post by jatin2 on 2014-08-12
I had gone through the [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) , as being not very techy guy it will take me long to understand the whole procedure. In the meanwhile, somebody advised me using Stellar Data recovery software. What do you think is it a good software?

---

### Post by Sef on 2014-08-12
> [COLOR=#000000]In the meanwhile, somebody advised me using Stellar Data recovery software. What do you think is it a good software?[/COLOR]

It does have some nice [reviews]("https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=stellar%20data%20recovery%20reviews").

---

