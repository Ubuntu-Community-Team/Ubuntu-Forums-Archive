---
title: "Installing Ubuntu and XP on the same hard drive"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by jayvan913 on 2006-04-29
If I installed both XP and ubuntu on the same hard drive would they work fine or get screwed up.

If it would work how would would I do it? Install XP first?

By the way I would be using an older Dell Inspiron 8600 notebook with a 40gb hard drive

---

### Post by bluevoodoo1 on 2006-04-29
They will work together fine! Install XP first. Remember, Ubuntu cannot write to an NTFS partition. 

check out this link!
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
(I've use it for Ntfs / Ubuntu dual boot)

---

### Post by Manveru913 on 2006-04-29
Theres probably a bunch of ways to do this, my favorite is as follows though:
Install Xp on a 10gig or so partition (you wouldnt think it would need to be this big, but i have it on a 5gig and its always running low, with just the os files). Next install Ubuntu on a similar sized partition, and have it set up your bootloader automatically-this has always worked for me. Now format the rest of your hd as a fat32 partition, so both OSes can use the one file partition, bingo. Now, Ive only done this using two separate harddrives, and you might need to install ubuntu first if youre only using one, im not sure.

---

### Post by Gannin on 2006-04-29
But, Linux can read from an NTFS partition.  Depending on what filesystem you choose for the Linux partition, there are also some Windows programs that can read from, and sometimes write to, Linux partitions.

---

### Post by Manveru913 on 2006-05-01
I thought ubuntu could only write and modify fat32 partitions. I heard there were some programs that might be able to do NTFS, but they were experimental and potentially dangerous. Maybe Dapper can write to NTFS?

---

### Post by Gannin on 2006-05-01
Not that I know of.  Ubuntu can read NTFS partitions, and read from and write to fat32 partitions.  There are some Windows programs that, when used from within Windows, can read from an ext3 partition, and some of them can read from and write to an ext3 partition.

---

### Post by manicka on 2006-05-01
You'll find some handy information on dual booting windows and ubuntu here

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by AmitAgrawal on 2008-01-20
I've found the guide at this somewhat useful [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
It's too late here...need some sleep probably will complete the install after returning from college tomorrow!

---

### Post by rosegarden78 on 2008-01-20
Yeah install Windows first.  Then Install Ubuntu.  Create another primary partition when asked (about 50%) and use this for Ubuntu.  No brainer.  My laptop's an Inspiron 1200 with 40Gb.  You may be pleasantly surprised by the results.  Say Yes when it asks to auto configure grub.

---

