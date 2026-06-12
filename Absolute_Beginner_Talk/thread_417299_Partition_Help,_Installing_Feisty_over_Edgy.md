---
title: "Partition Help, Installing Feisty over Edgy"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Median on 2007-04-21
Hi everyone, right now I've got Edgy installed on a partition and I'm dual booting with Windows XP on another partition.  I'm trying to install Feisty off of the Live CD and I was wondering if it was possible to simply write over the current Linux Ext3 partition that I have Edgy on? I've been trying to do this manually through Gparted but every time I select that partition, click the Format checkbox, and try to go forward with the install I get a "No root file system is defined.
Please correct this from the partitioning menu." message.  Can anyone help me out here?

---

### Post by Campingman on 2007-04-21
This is a little vague as I cannot remember exactly what the boxes are called.  You have to define which partition is to be used as the root, in Gparted manual edit preferences there are two drop down selection menus one is for ext3/fat etc the other is the one you need to define the partition.  to define it as root select   /
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)   
Gives more advice on partitions required
Hope this helps

---

### Post by Median on 2007-04-21
Ah great, thanks.  I had to just right click the partition and choose to edit it, the drop-down menus were in there.  Thanks again!

---

