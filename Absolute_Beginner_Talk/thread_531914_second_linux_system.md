---
title: "second linux system"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by calymea on 2007-08-22
is it possible to have second linux system dual - booted with Ubuntu? If so could someone detail the process. Thanks to all.

---

### Post by rich.bradshaw on 2007-08-22
Essentially, install on spare partition.

Edit grub.

---

### Post by hyper_ch on 2007-08-22
yeah, you just need another partition and you can use the swap partition for both installs...

---

### Post by calymea on 2007-08-23
Thanks for the reply, could you tell me how to create the required partitions please?
thanks again.:)

---

### Post by Dark Star on 2007-08-23
Use Gaprted [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) to create a new partiotion ..:) and instal an OS in it.. The Grub will automatically install the OS menu in it :)

---

### Post by Calash on 2007-08-23
Be careful when adding, resizing, and general adjusting your partitions.  You do run the risk of deleting all your current data if you try to rush through the process and do not pay attention to what you are doing.

Take your time and make sure everything is good before applying the changes.

Backing up your data, just to be safe, is a good idea.


You can also add another hard drive to your system and install the second Linux on that if you do not want to be bothered with partitioning.

---

### Post by Dark Star on 2007-08-23
> **Calash said:**
> Be careful when adding, resizing, and general adjusting your partitions.  You do run the risk of deleting all your current data if you try to rush through the process and do not pay attention to what you are doing.

Take your time and make sure everything is good before applying the changes.

Backing up your data, just to be safe, is a good idea.


You can also add another hard drive to your system and install the second Linux on that if you do not want to be bothered with partitioning.
Yep backing should be the 1'st thing before doing any partition stuff or you can loose the data by wrong step :p

---

### Post by Calash on 2007-08-23
Agree 100%.  I see way to many posts here about people losing data due to quick partitioning.  A backup of any important data is very important, and not just when performing something as altering as partitioning.  Hard drives do not last forever, and when one fails it is too late to get your data off.

Well, data recovery is always an option...but at $5000 it can be out of the range of some people.

---

### Post by hyper_ch on 2007-08-24
Partitioning is not really hard but two things must be taken care of:

(1) BACKUP YOUR DATA!
(2) READ WHAT THE PARTITIONER IS ACTUALLY SAYING

That way you shouldn't have problems.

---

