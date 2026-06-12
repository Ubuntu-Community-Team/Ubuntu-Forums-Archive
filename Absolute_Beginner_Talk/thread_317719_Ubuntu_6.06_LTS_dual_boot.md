---
title: "Ubuntu 6.06 LTS dual boot"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by sachincool on 2006-12-12
I have winxp installed
i have started installing dapper for dual booting and ve come upto partitioning
but its showing me only2 options
1.completely erase h/d
2.manually edit partition

i selected 2nd one now its not showing me partition table
its showing me only one partition
what could b the problem
pls help me

---

### Post by confused57 on 2006-12-12
Here's an excellent guide, with screenshots, for installing with the desktop cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Make sure to defrag your Windows partition several times before resizing it.
Backup any important data you don't want to lose first.

---

### Post by sachincool on 2006-12-12
ok but according to the link there r 3 options in the partition
window
but on my machine its showing only two

---

### Post by Qrk on 2006-12-12
Why don't you try edgy? Dapper has some issues resizing windows partitions as it is.

---

### Post by sachincool on 2006-12-12
ok but i am a newb and i just want to try any linux os and i have dapper cd, for gettin edgy i have to dwnload it

---

### Post by sachincool on 2006-12-12
isnt there any slution for my  dapper problem

---

### Post by Qrk on 2006-12-12
Well, if you don't want to download a large ubuntu cd, try something like the gparted live cd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) to partition, and then install Ubuntu using your Dapper cd. 

Or you can try the alternate install cds of Ubuntu, which are available on the Ubuntu webpage.

Unforunatly, I've never heard of your problem, so I can't really give you an easy answer.

---

### Post by sachincool on 2006-12-12
ok i will try this
thanx

---

### Post by sachincool on 2006-12-12
i saw the alternete cd specifications its 69 mb that means it can not install the whole system then pls tell me the procedure to install it from the alternate cd 
i mean to say the key point while using alt cd

---

### Post by Qrk on 2006-12-12
You wouldn't use the gparted cd to install Ubuntu, only to do the partitioning step. Once you've partitioned your drive, Ubuntu will install just fine. So the steps would be ...

1) Boot up the gparted liveCD
2) Reduce the size of Windows using gparted, (leave the rest as free space)
3) Boot up into Dapper,
4) Tell Ubuntu to install on the Free space. 

This would only require you downloading the gparted Live cd, which at 28.5 MB, is very small.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by sachincool on 2006-12-12
i got it 
thanx
sachin

---

