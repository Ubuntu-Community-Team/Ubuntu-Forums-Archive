---
title: "Dual Boot"
date: 2011-07-02
forum: Apple Hardware Users
---

### Post by photochuck on 2011-07-02
How much space do I need to have a dual boot.

---

### Post by oldfred on 2011-07-02
How much do you have?:)

Ubuntu's absolute minimum is a little over 4GB of hard drive space. I typically recommend 10 to 20GB depending on how much you want to add in the way of software. Of course /home includes all your data which can be anything from nothing to TBs of data.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html)

---

### Post by photochuck on 2011-07-03
Thank you for your reply. I have over 60GB right now. I could move some things to an extern HD and get that up to about 75GB. Thanks again for your reply and the links.:)

---

### Post by oldfred on 2011-07-03
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Herman has lots of info on dual booting. Only slight difference in screens if installing a different version than his examples with screenshots. Not as complex as it may seem at first as he has lots of detail and links to additional info.
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)


GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

