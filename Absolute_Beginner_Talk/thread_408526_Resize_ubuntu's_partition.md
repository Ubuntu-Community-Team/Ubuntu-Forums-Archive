---
title: "Resize ubuntu's partition"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by tiendn on 2007-04-13
Hi!
 I installed Ubuntu on my computer, and I want to know how can I resize ubuntu's partition for installing one different OS.
                                                                                               thanks!

---

### Post by Seisen on 2007-04-13
You can use Gparted Live Cd to do that. Here is the link.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by rgd55 on 2007-04-13
Here is a couple more,

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

### Post by synthsrkl on 2007-06-06
i am thinking of doing a similar thign

even if i resized my current ubuntu partition, would my installation and files remain?

---

### Post by LaRoza on 2007-06-06
Yes.

---

### Post by Romin-1 on 2007-06-06
Which version of gparted would I use for Dapper Drake? Source Forge has many listed.

Thanks kindly,

Jon

---

### Post by meng on 2007-06-06
If you want gparted on dapper, the following should work:
sudo apt-get install gparted

---

### Post by diatribe on 2007-06-06
[http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-7.iso?modtime=1179575456&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-7.iso?modtime=1179575456&big_mirror=0)

that is the one to download

---

### Post by diatribe on 2007-06-06
also if he installs gparted he won't be able to resize his partition, you can't edit mounted partitions thats why he needs the livecd

---

### Post by strabes on 2007-06-06
You can only resize non-mounted partitions so if you install gparted onto ubuntu and then try to resize your ubuntu partition it won't work.

---

