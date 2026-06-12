---
title: "PC set up help"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by olddave on 2006-07-12
Hope some one can give me Advice.
Here is my set up at the moment,
C/drive = Windows XP 
D/drive = empty
E/drive = Programe files
CPU = P4 2.8
RAM = 512
GRAPHICS CARD =  ATI gigabyte radeon 9600pro.
can i install ubuntu 6.06 on the d drive an duel boot with windows,
What will the partion table look like in the install windows and
witch HDA will be my old D drive.
Thanks olddave

---

### Post by dmizer on 2006-07-12
is the d drive completely unformatted free space, or have you formatted via windows?

easy answer to your question is ... yes, it's absolutely possible, you will just have to be very careful.  if you have the live cd, it would be important to boot into the live version of ubuntu and take a look at what ubuntu calls the two drives.  that way you can have an idea of what to expect when you go for the actuall install.

---

### Post by houstonbofh on 2006-07-12
> **olddave said:**
> Hope some one can give me Advice.
Here is my set up at the moment,
C/drive = Windows XP 
D/drive = empty
E/drive = Programe files
CPU = P4 2.8
RAM = 512
GRAPHICS CARD =  ATI gigabyte radeon 9600pro.
can i install ubuntu 6.06 on the d drive an duel boot with windows,
What will the partion table look like in the install windows and
witch HDA will be my old D drive.
Thanks olddave

Is that 3 drives, or 3 partitions?  If partitions, how big is partition one?  If it is partitions, and "C" is very large, you may not be able to boot if the "/boot" mount is to far away from the beginning of the drive.

However, if you can get it going, the default will be slower than you can be.  The newer 686-SMP kernel will give you a performance boost, and the graphics card has an optional high performance driver.  Look (or ask) for these when you get going.

---

### Post by richbarna on 2006-07-12
> **olddave said:**
> Hope some one can give me Advice.
Here is my set up at the moment,
C/drive = Windows XP 
D/drive = empty
E/drive = Programe files
CPU = P4 2.8
RAM = 512
GRAPHICS CARD =  ATI gigabyte radeon 9600pro.
can i install ubuntu 6.06 on the d drive an duel boot with windows,
What will the partion table look like in the install windows and
witch HDA will be my old D drive.
Thanks olddave

Are these "physical harddrives" or "partitions" ?
If they are physical harddrives, you just install to "D" and make sure that you put the Grub installer "boot" on drive "C", you will have :-
C - Grub and Xp
D - Ubuntu Root + Swap
E - Program files

If they are only partitions :-
C - Grub +Xp
D - An extended partition with Root + Swap inside it (you can't have more than 4 primary partitions on one harddrive, however you can put logical partitions in an extended partition)
E - Program Files

I hope that helps

---

### Post by olddave on 2006-07-12
Hi all this is a 120 gig drive with partions,i have no idea about   4 primary partitions. i have installed ubuntu 5 on an old pc but this is going to be on MY MAIN PC so all HELP will be of help. What about ATI graphics cards.
thanks olddave

---

### Post by richbarna on 2006-07-12
> **olddave said:**
> Hi all this is a 120 gig drive with partions,i have no idea about   4 primary partitions.

If they are only partitions :-
C - Grub +Xp
D - An extended partition with Root + Swap inside it (you can't have more than 4 primary partitions on one harddrive, however you can put logical partitions in an extended partition)
E - Program Files

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

The best way is with the Dapper live cd (desktop).
Use gparted (gnome partition manager) to format Partition D
Select the partion then choose to fromat as an extended partition.
I light blue border will appear around the partition.
Click the inside of the partition and choose creat a partition, this time you choose SWAP which usually is about 512Mb. 
Now choose to format the other free space as Ext 3, save and exit.

When installing Ubuntu it will ask you to choose 2 partitions for the install, "/" will be the root (main installation) then Swap.
When it's time to install grub, you just let it overwrite the windows MBR at the beginning of drive C.

---

