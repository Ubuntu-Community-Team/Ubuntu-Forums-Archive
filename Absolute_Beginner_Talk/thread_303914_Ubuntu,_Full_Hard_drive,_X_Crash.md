---
title: "Ubuntu, Full Hard drive, X Crash"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-11-21
Hi there,

This is the second time that this has happend. On the first ocasion  I deleted an anormouse mpg and when I restarted the machine the following morning I got an error saying that X has failed to load. Viewing the log file it cannot write two files to the disk. 

Back in windows I see that the drive that Root is mounted in is full. 

Can anybody reccomend an app in either windows or linux(must be text based) which I can use to find the sinfull file as I cannot find it by hand. Something like a drive usage meter which will scan the drive folder by folder.

Thanks,

Rudolf

PS: Any other plans or suggestions are welcome.

---

### Post by aysiu on 2006-11-21
I don't know about the offending file, but you could probably free up some space by booting into recovery mode and typing ```
aptitude clean
reboot
``` That will clear out you /var/cache/apt/archives directory.

---

### Post by anaconda on 2006-11-21
The big mpg file that you deleted is propably still in your /home/xxx/.Trash -folder.
or in /lost+found -folder or if it was in different partition/drive then it is there in /lost+found

Just empty your trash, and you will get lots of room back.

---

### Post by thomasbechtold on 2006-11-21
hi,

you can also delete you cache for the packages.

go to /var/cache/apt/archives

and then delete all files with ending .deb
you don't need this files & if you will need them, apt(or synaptic) will download the files for you again.

so do:
"cd /var/cache/apt/archives"
"sudo rm -f *.deb"


If you want to know how much space if left on a partition, do:

"df -h"


cheers tom

---

### Post by RudolfMDLT on 2006-11-21
Hi there! After the first ocasion i remounted my HOME directory(thanks to aysiu's guide) on a diffrent partition to keep this from happening. On the previouse ocasion I could empty the trash and that did the trick. 

Now, some file somewhere has just went and got written off the partition and I just need to find it. Any way of finding large files in Ubuntu as I cannot track it down? In Kubuntu there is an application for this purpose but I can't get there! :)

Thanks,

Rudolf

---

