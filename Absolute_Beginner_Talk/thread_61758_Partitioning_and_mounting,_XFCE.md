---
title: "Partitioning and mounting, XFCE"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by rajsarkar on 2005-09-02
Hi friends,

As an absolute beginner I am facing lot of problems. I have installed Hoary in my PC(celeron 500 MHz). Have the following partition:

hdb1        pri          8GB         ext3
hdb2        pri          8GB         ext3
hdb3        pri          1GB         swap
hdb5        log         8GB         ext3
hdb6        log         8GB         ext3
hdb7        log         7GB         FAT32

Hope the partitioning is alright. My idea was to do some experiment and learn by installing severel OSs at different partitions. 

Now the problems:

1. Installed only Hoary on hdb1. Not able to see other partitions (may be I don't know how to see it). Except hdb1 and hdb7 I have not mounted the partitions during the partitioning process.

2. For hdb7 the installer did not allow to leave it unmounted. So i had to mount it as Windows. Shall I still be able to see common files in this partition from different 
OSs

3. I am desparately looking for some guide meant for beginers. I studied and practiced a lot during last few weeks. But still some fundas like mounting, sudo etc are not clear. Pls inform some good references (free ofcourse).
 
4. I installed xfce along with some multimedia program from ubuntuaddon cd provided by mrbass.org. Now with XFCE I can't access CD drive. How can I solve it?

Thanks and regards,

Raj

---

### Post by aysiu on 2005-09-02
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by rajsarkar on 2005-09-02
Hi aysiu.

Thanks a lot.

Got a lot of help from Ubuntuguide. However some are still unanswered. 

1. How can automatically mount other ext3 partiions during boot-up?
2. regd XFCE: The mounting problem may be inherent in XFCE. Am I right?

Regards,

Raj

---

### Post by xmastree on 2005-09-02
[QUOTE=rajsarkar]1. How can automatically mount other ext3 partiions during boot-up?[/QUOTE]Include them in /etc/fstab and they'll be mounted at bootup.
You'll need to make individual mount points for them.

---

