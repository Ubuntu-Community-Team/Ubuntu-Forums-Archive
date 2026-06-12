---
title: "Partitioning help needed"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by e6626550w on 2007-07-01
I've been trying to follow the tutorial from psychocats on creating a separate home partition after Ubuntu has been installed. I follow it fine after booting from the live CD and bringing up Gparted. My question is this, the author cautions strongly about making sure that the partitions are named correctly and what I get after I've resized /dev/sda1 and told the program that the unallocated partition was new is something like "New 1" or something close to that. I expected for it to name it it /dev/sda* not just New 1 ( I think that is what it said). In the tutorial the /dev/hda5 was shrunk and the new one created named by Gparted /dev/hda7. Could this possibly be correct that my new partition is called New 1? 

Obviously I know nothing about partitioning or I wouldn't be asking but thanks in advance for any help I do get.

eileen...

---

### Post by Computer-Geek on 2007-07-01
In DEV folder the partition name couldn't b New 1 it should be starting with sda,sdb,hda or hdb. Try to see which one is there and if the partition u created u have given mount point /windows then it should be mounted in folder windows present in rot dir.

Thansk!!

---

### Post by nanotube on 2007-07-01
> **e6626550w said:**
> I've been trying to follow the tutorial from psychocats on creating a separate home partition after Ubuntu has been installed. I follow it fine after booting from the live CD and bringing up Gparted. My question is this, the author cautions strongly about making sure that the partitions are named correctly and what I get after I've resized /dev/sda1 and told the program that the unallocated partition was new is something like "New 1" or something close to that. I expected for it to name it it /dev/sda* not just New 1 ( I think that is what it said). In the tutorial the /dev/hda5 was shrunk and the new one created named by Gparted /dev/hda7. Could this possibly be correct that my new partition is called New 1? 

Obviously I know nothing about partitioning or I wouldn't be asking but thanks in advance for any help I do get.

eileen...

please post a screenshot. i'm not sure at what point it is actually saying "new 1" for you...

---

### Post by mikewhatever on 2007-07-01
There is no such thing as an unallocated partition, it's just unallocated space. Once a partition is created, it should be named what you've expected.

---

### Post by e6626550w on 2007-07-01
I can't do it right now but I certainly appreciate the help. Tomorrow i'll post some screenshots and if you run across my post, hopefully you'll be able to mentor me a bit. I didn't think what I was getting made any sense. Glad I ask before I went ahead and messed everything up. Thanks again.

eileen...

---

### Post by frazelle09 on 2007-07-01
i just used GParted again and had the same experience.

Resizing and "setting" a new partition is a two-step process.  In step one you resize the partition.  The program usually take a while to resize and when it finishes you have your original partition and a big "space" to the right of the original partition.  If i remember correctly this big space is called New1 or something like that.  i think that GParted gives it a "temporary" name so you can identify it and work with it.

In the second step you need to tell GParted that you want that big space to be a new partition.  You do so by selecting the big space and using one of the drop-down menus.  Select Partition.  It should also offer you the option of formatting it to a certain file type.  i think Ubuntu uses "reiserfs".  Choose this and then use the button in the Task Bar at the top which says Apply.

Now! you should end up with your sda1 and sda2 partitions.  Check the name of your first partition.  It should be something like sda1, so your new partition will be sda2!

Hope this helps and have a great evening!  :)

---

