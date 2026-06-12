---
title: "[SOLVED] hd format for ubuntu"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by nathan1936 on 2007-12-22
Hey just a quick question. 
I have my harddrive formatted to fat32, but ubuntu wont install on it.
I can get the live cd to go, and in GParted it tells me I have two extra partitions: 
1 is extended and 1 is linux swap, both about 1.2 gbs.
For partition it says /dev/sda2, and the other says /dev/sda5
And the new partition that I can format to anything. WHAT DO I WANT IT AT?
I have tried installing this all day, it just hasnt worked yet...
The new partition is 26.75gb

Everytime I install, it seems the installer ends prematurely 
any advice...

Is there some preperation im forgetting to do?

---

### Post by Sef on 2007-12-22
To install Ubuntu, use the default format: ext3.   

Set up the partitions this way:

/ (root - where Ubuntu goes): 8-10 GB

/swap - 1 1/2 times your ram (If your ram is 1 GB or more, then 1 GB swap is all that is needed.)

/home (where your files reside) - the rest of the partition.

Both / and /home can be set as ext3.

---

### Post by nathan1936 on 2007-12-22
Ok I formatted and got the 9.77gb ext3 [where ubuntu goes] 
But how do you name them like you said? It said its /dev/sda1 
Also 307.28 mb are being used? whats that about?
I dont see the /swap anywhere... but i think the /dev/sda2 and 3 are the same amount as my ram does that mean thats what they are?
Sorry Im new to this, I switched from vista because it sucked. :lolflag: but thanks

---

### Post by tylerspaska on 2007-12-22
sef, what is the reason you put root and home on different partitions? in case you need to reinstall? i've always put eveything on the same partition, but maybe this has been dumb of me.

---

### Post by nathan1936 on 2007-12-22
On the partition 9.77gb, i found out what the 300 mb's is. It is a file called lost+found that I dont have permission to access. Any idea what I should do?
I think its a fragmented install of ubuntu but i dont know for sure.
What do you think?

---

### Post by Sef on 2007-12-22
> sef, what is the reason you put root and home on different partitions? in case you need to reinstall? i've always put eveything on the same partition, but maybe this has been dumb of me.

Not a dumb question.  Yes in case of reinstall, a clean install or something crashes your system your home files should be ok.  Still it is a good idea to back your home file before any installation.

> On the partition 9.77gb, i found out what the 300 mb's is. It is a file called lost+found that I dont have permission to access. Any idea what I should do?
I think its a fragmented install of ubuntu but i dont know for sure.
What do you think?

You are right.  Here is something from [Linux Filesystems Hierarchy]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html").

---

### Post by nathan1936 on 2007-12-23
So what do I do to delete it? When I run the installer, now it says i cant install... Should I just install on the whole disk?

---

