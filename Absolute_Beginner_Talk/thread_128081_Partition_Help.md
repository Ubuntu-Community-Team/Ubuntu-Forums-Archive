---
title: "Partition Help"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by Glass_Onion on 2006-02-10
I need help sorting out my partitions. I've got Ubuntu installed on SDA4 and am wondering if I can move that to under SDA3 with the swap and fat32 partition. I'm also wondering what the fat32 partion is and could anybody tell me? I'm not quite sure what's on it but I know I don't need it to be quite that big. I've uploaded a screenshot of them from GParted to TinyPic if that can help in someway. Thanks in advance. :)

[http://i1.tinypic.com/ngyat3.png](http://i1.tinypic.com/ngyat3.png)

---

### Post by cjm5229 on 2006-02-10
It Looks like sda1 is your windows rescue partition, sda2 is windows partition, sda4 is Ubuntu partition. Now you have a rather large empty space which is doing nothing, so you need to try to resize your ubuntu partition to use up that space. You may need to use gparted on a live CD to do that. Actually I have found that QTparted on the Mepis live CD works the best for me. You can use Knoppix or Ubuntu live CD's also. The swap partition is Ok, and I'm not sure what is on sda5, it looks like an empty fat32 which is good. That can be used to tranfer files back and forth between Linux and windows. You could also format that empty space as ext3 and mount as home for Ubuntu. Hope this helps.

---

### Post by Glass_Onion on 2006-02-11
Thanks, That's pretty much what I knew. I was just looking for help though on how to move my Ubuntu set-up over to that FAT32 partion after formating it. :) Any help or a howto link would be much appreciated.

---

### Post by aysiu on 2006-02-11
[QUOTE=Glass_Onion]Thanks, That's pretty much what I knew. I was just looking for help though on how to move my Ubuntu set-up over to that FAT32 partion after formating it. :) Any help or a howto link would be much appreciated.[/QUOTE] PartImage.

Load up the Ubuntu live CD and then ```
sudo apt-get update
sudo apt-get install partimage
sudo partimage
``` Then copy one partition to the other.

---

