---
title: "Warning! while partitioning hard drive for Dual Boot"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by parkerfutbol3 on 2008-03-02
I have two 250GB hard drives, one has my Windows installed on it, the other I wish to install a 50BG partition for Ubuntu. I popped the livecd in and everything seemed to be working well enough.

I went in to manually partition my second drive which now at the partition manager looks like this:

/dev/sdb
/dev/sdb1  fat16  /media/sdb1   49MB        33MB
/dev/sdb2  ntfs    /media/sdb2  200005MB  3200MB
[B]/dev/sdb5  ext3    /                   48002MB   unknown
/dev/sdb6  swap                       1941MB     unknown[/B]

Now when I go to create these partitions I get this message:

"File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 24026 (47959 expected); size of FATs is 94 sectors (188 expected)."
With options to "ignore" or "cancel"

I don't have total executive control over this computer as it "belongs to the family", thus I am reluctant to simply ignore this warning and risk losing data from Windows which everyone else uses. Anybody have anything??

Thank you in advance.

---

### Post by louieb on 2008-03-02
If the partition is a logical partition that message is normal. Don't know why it pops up. 

Which partition editor are you using? THe one in the installer or the one under System>administration>Partition Editor?

---

### Post by parkerfutbol3 on 2008-03-02
I was using the partitioner that is part of the Installer, I'm assuming Gparted is a bit more graphical so I guess i will try that now.

---

### Post by owbizi on 2008-03-02
Well, [apparently](http://ubuntuforums.org/showthread.php?t=475618) this error has no real importance. Repeating, apparently...

Do you use a Dell computer too?

---

### Post by parkerfutbol3 on 2008-03-02
Yes I do! I just used Gparted instead and successfully created the partitions and will soon be attempting to install onto those

---

### Post by owbizi on 2008-03-02
Well, so... be welcome to Ubuntu! Enjoy the experience. :)

---

### Post by Papa-san on 2008-03-05
Just to make sure, I ended up going to [http://www.onlineconversion.com/computer_base2.htm](http://www.onlineconversion.com/computer_base2.htm) to be sure my sizes were right. Even after adding the right number of MB, I still got the error... I ignored it, and have explained to my daughter that if there is a problem, we will be running the Ubuntu installer that cleans out the Vista Virus completely from her computer...

Yes, it is a pre-loaded Dell. (I couldn't convince her to just go with the Ubuntu version...)  :-(

---

### Post by Kiri on 2008-03-05
I think that error is because of the fat16 dell 'recovery partition' at the beginning of the disk...

---

