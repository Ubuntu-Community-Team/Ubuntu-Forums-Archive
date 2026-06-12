---
title: "resizing the active partition"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by missed her show on 2008-01-02
so i'm ditching the windows completely after my entire pc existance of, oh 15 or 20 years.    Have started to love Macs, then i found ubuntu and it's been greater than great.

My 20 gb hd is split into two partitions,  ubuntu partition and then the XP partionion.   I'm bottoming out on my ubuntu disk, runnning out of space FAST.   All of my data is kept on an external hdd.  

i want to format/delete the XP partition and merge it with the Linux partition, giving me the entire use of the disk for linux.

How can i do this from within ubuntu?   or do i need to boot from the install cd?

---

### Post by kpkeerthi on 2008-01-02
I suggest you use Ubuntu Live CD. 
Boot with the Live CD, run **gksudo gparted**. Just delete the XP partition, resize your ext3 partition and **Apply** the changes. Finally, you may want to [restore GRUB]("http://ubuntuforums.org/showthread.php?t=24113")

Good luck.

---

### Post by missed her show on 2008-01-02
thanks for the quick reply  i'm gonna give that a shot.

---

### Post by dcstar on 2008-01-02
> **missed her show said:**
> so i'm ditching the windows completely after my entire pc existance of, oh 15 or 20 years.    Have started to love Macs, then i found ubuntu and it's been greater than great.

My 20 gb hd is split into two partitions,  ubuntu partition and then the XP partionion.   I'm bottoming out on my ubuntu disk, runnning out of space FAST.   All of my data is kept on an external hdd.  

i want to format/delete the XP partition and merge it with the Linux partition, giving me the entire use of the disk for linux.

How can i do this from within ubuntu?   or do i need to boot from the install cd?

It is also a good idea to have a separate /home partition (which holds all of your user files). This way you can install/reinstall a Ubuntu version and not lose any of your valuable data.

There are detailed instructions in the forums on how to set up a separate /home partition.

---

