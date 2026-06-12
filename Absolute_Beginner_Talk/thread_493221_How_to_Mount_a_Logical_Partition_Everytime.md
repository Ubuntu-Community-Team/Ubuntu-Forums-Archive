---
title: "How to Mount a Logical Partition Everytime?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by GG_HTPC on 2007-07-05
I have created a 300 GB logical partition in my HDD. This partition is set as the destination for MythTV. Every time I reboot my machine, I have to manually mount the partition. Because of this I have to restart MythTV every time as well. 

Can anyone please advise how to avoid manual mount and restart?

Thank you

---

### Post by kinematic on 2007-07-05
how to mount a partition has been answered countless times before(doesn't matter if it's a logical partition).....do a forum search or use google.

---

### Post by annda on 2007-07-05
put the partition in /etc/fstab

here are two links: basic instructions
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

and a lot of info on mounting and fstab:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Moop on 2007-07-05
Here you go.
[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by stchman on 2007-07-05
> **GG_HTPC said:**
> I have created a 300 GB logical partition in my HDD. This partition is set as the destination for MythTV. Every time I reboot my machine, I have to manually mount the partition. Because of this I have to restart MythTV every time as well. 

Can anyone please advise how to avoid manual mount and restart?

Thank you

use my procedure to mount partitions using your fstab file.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

Hope this helps.

---

### Post by GG_HTPC on 2007-07-05
Thank you, Thank you!

---

### Post by Dipper on 2007-08-11
How would I go about editing this file graphically?  I'm CLIphobic.

---

