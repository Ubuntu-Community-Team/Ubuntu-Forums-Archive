---
title: "Need help to dual boot."
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Dysan on 2007-05-16
I want to be able to have both Ubuntu and Windows XP on my computer, but whenever I try to install one of them, they automatically reformat the entire thing. I've looked on google about this, and I'm only finding little guides about being sure to back up the data I want to keep, blah, blah, blah, stuff I'm not looking for.

Help?

---

### Post by Najand on 2007-05-16
Install Windows First. During Windows Installation make 2 partitions and format the first one as "NTFS" to install Windows on it. Then Install ubuntu... And during installation, when it comes to partitioning, select "Manual Partitioning" and then select the second partition and make two partitions: an "EXT3" filesystem one to install ubuntu on it and another one as "Linux SWAP" (Well, SWAP should be approximately twice the size of your RAM). And follow the process of installation with that.

---

### Post by stefaan.dutry on 2007-05-16
> **Dysan said:**
> I want to be able to have both Ubuntu and Windows XP on my computer, but whenever I try to install one of them, they automatically reformat the entire thing. I've looked on google about this, and I'm only finding little guides about being sure to back up the data I want to keep, blah, blah, blah, stuff I'm not looking for.

Help?

In order to make a dual boot system you need at least 2 partitions on your harddisk.
installing an operating system it thinks it can use the whole selected partition.

I suggest installing windows xp first, and then Ubuntu, because then it will automaticaly make a multi boot startup when installing the ubuntu.

I hope this was of any help to you

---

### Post by tompickles on 2007-05-16
just a thought - definatly install XP first, and then Ubuntu. And create your 2 partitions in the XP install. What I would recommend is that when you are in the "Manual  Partitioning" part of the Ubuntu setup you create an EXT3 partition for ubuntu (/), a 2nd EXT3 partition for your Home Directory, and a Linux Swap. This means that when Gutsy rolls along, you can do a complete clean install of the operating system and not loose all your data, as they are on different partitions!

Hope this helps!

---

### Post by zvacet on 2007-05-16
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

