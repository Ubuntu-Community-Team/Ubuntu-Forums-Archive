---
title: "Making Partition Primary,  Active or Logical"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by JerryAtrik on 2007-04-11
I have acronis Partition Expert to divide my blank partition into 4 sections ie 
( 1 ) Ubuntu OS 
( 2 ) Ubuntu home  --Shared data
( 3 ) Swap file
( 4 )  Windows XP

I am not sure whether the Swap file should be logical or primary
Can anyone please advise
Cheers jerry

---

### Post by annda on 2007-04-11
why not use the ubuntu cd to do the partitioning? it is part of the installation.

make one primary partition for one of the OSes and put the rest on extended partitions. swap can be a logical disk, it doesn't need a separate partition.

hope this clears things up.

---

### Post by annda on 2007-04-11
also, are you planning on installing windows on the last partition, or just using it for windows storage?

if you want to install, start with windows. then you can use the ubuntu cd to shrink the win partition and divide the rest of the disk however you like.

---

### Post by JerryAtrik on 2007-04-11
Cheers Annda Windows is already on first partition now have empty partition beside it .It was mainly the swap file I was concerned about I thought as it is part of the Ubuntu install it might need a primary or active partition .You have now cleared it up nicely for which I thank you .I did not think the installer on Ubuntu would do more than two partitions thats why I went for a freelance Partitioner.
Thank you again 
Jerry

---

