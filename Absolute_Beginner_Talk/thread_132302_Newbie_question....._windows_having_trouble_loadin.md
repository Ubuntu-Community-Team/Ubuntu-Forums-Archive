---
title: "Newbie question..... windows having trouble loading after installing Ubuntu"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by depu on 2006-02-18
Hello ppl. To start off with, i am an absolute newbie at Linux so pardon me if i ask somethng stupid :) but ever since i installed ubuntu Windows takes about 5 mins more to load up.
I have 2 HD's 80Gb and a 20Gb one while the 80 Gb one i have for Windows 2000 i run Ubuntu on the second Hd i.e the 20Gb one. Before installing Ubuntu the 2nd HD had two partitions H and I and while installing Ubuntu i erased the entire 2nd HD and now it has two partitions one for ubuntu and the second for swap. Now whenever i boot up into windows it stops and checks the 2nd HD and says that the H partition is supposed to be FAT32 and asks whether i want to perform a disk check. Even after that the loading slows down a lot and it takes near a minute to loadup. Now even the "My Computer" screen takes a  looong time to load up and it keeps searching for something and goes unresponsive.
can someonehelp me on this?

---

### Post by depu on 2006-02-21
can somebody help me with this??

---

### Post by Kapre on 2006-02-21
[QUOTE=depu]Hello ppl. To start off with, i am an absolute newbie at Linux so pardon me if i ask somethng stupid :) [/quote] 

depu - 1st of all there is no such thing as stupid questions. 2nd, please be patient as some people might have looked into your problem and is now trying to answer them.

>  but ever since i installed ubuntu Windows takes about 5 mins more to load up.
I have 2 HD's 80Gb and a 20Gb one while the 80 Gb one i have for Windows 2000 i run Ubuntu on the second Hd i.e the 20Gb one. Before installing Ubuntu the 2nd HD had two partitions H and I and while installing Ubuntu i erased the entire 2nd HD and now it has two partitions one for ubuntu and the second for swap. Now whenever i boot up into windows it stops and checks the 2nd HD and says that the H partition is supposed to be FAT32 and asks whether i want to perform a disk check. Even after that the loading slows down a lot and it takes near a minute to loadup. Now even the "My Computer" screen takes a  looong time to load up and it keeps searching for something and goes unresponsive.
can someonehelp me on this?

How did you format your swap? It seems like M$ is still sees it as FAT32 because it was not formatted well. Maybe there is still space left on the 2nd HD that was not formatted that is why M$ is telling you that it's supposed to be FAT32. Run defrag on your M$ and also check if the 2nd HD was formatted correctly.

K

---

### Post by frodon on 2006-02-21
When you boot on linux and mount your partitions do you see any errors, i got the same problem before my HDD crashed.
Also try to know what is the name of your partition under linux : hda or hdb or hdc or hdd. And run this command, try for each one if you don't know the name of your drive under linux : ```
sudo fdisk -l /dev/hda
```Then paste the result for your HDD here, i will see if your partition table looks good.

---

### Post by depu on 2006-02-21
sorry about being impatient ...just that its pretty annoying to wait for over 3 mins when ur OS loads.Also i had simply erased the enitre second disk when i was installing Ubuntu, a part of the disk was FAT32 before i installed ubuntu. The problem is that when ever i load any window that lists the disk drives it goes "Not Responding" same with the Defrag and  My Computer.
and fordon i had installed ubuntu on hdd and i have pasted the output of 
sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2484    19952698+   7  HPFS/NTFS
/dev/hdc2            2485        9696    57930390    f  W95 Ext'd (LBA)
/dev/hdc3            9697        9729      265072+   7  HPFS/NTFS
/dev/hdc5            2485        4950    19808113+   7  HPFS/NTFS
/dev/hdc6            4951        7424    19872373+   7  HPFS/NTFS
/dev/hdc7            7425        9696    18249808+   b  W95 FAT32

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2341    18804051   83  Linux
/dev/hdd2            2342        2434      747022+   5  Extended
/dev/hdd5            2342        2434      746991   82  Linux swap / Solaris

and thanks for responding i was begining to think that my post was lost among all the other mails

---

### Post by frodon on 2006-02-21
> The problem is that when ever i load any window that lists the disk drives it goes "Not Responding" same with the Defrag and My Computer.Do you mean under windows. If yes the problem don't come from /dev/hdd because you shouldn't be able to see it under windows execpt if you installed the ext3 drivers for windows.
So which partition generates the problem ? try to know its name and under linux run this command, i give you an exemple for hdc7 : ```
fsck.vfat /dev/hdc7
```It will check if your partition contains bad sectors which may generates this kind of problems, add the -a option to repair automaticaly bad sectors.

---

### Post by depu on 2006-02-21
Yes it does happen under windows and it tried to do a disk check for the H: drive which used to be FAT32 before i formatted it using the ubuntu installation also the disk listing in windows becomes Not Responding when it comes to that drive that is H:

did  fsck.vfat /dev/hdc7
gave 
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdc7: 13211 files, 891540/1140055 clusters
what do i have to give for the ntfs partitions?

---

### Post by frodon on 2006-02-21
I advice you to check all your partitions but i'm not sure that there is a tool for ntfs, maybe someone could give us more information on this point.
The problem is that i noticed that windows don't tell you that you have bad sectors on a partition it just give you some errors or freeze, try to get as many information as possible under linux and for your ntfs partition i'm sure there's a tool for windows to perform a check of the partition, maybe partition magic but i can't help you more with NTFS because i never add problems with NTFS partitions and therefore never needed  a tool to check a NTFS partition.

By the way, your partition table for hdd looks good but don't allow you to see your disk under linux because the extented partition (hdd2) is linux formatted but it's not a problem i think because you use this drive only with linux.

---

### Post by depu on 2006-02-21
ok will try to do that as well. thanks for the help

---

### Post by depu on 2006-02-22
will reinstalling Ubuntu help? am really bugged by this problem now coz even giving the directory path for mp3 in winamp made it hang.....
so i am wondering if i can simply insert the ubuntu cd and erase the disk and reinstall ubuntu

---

