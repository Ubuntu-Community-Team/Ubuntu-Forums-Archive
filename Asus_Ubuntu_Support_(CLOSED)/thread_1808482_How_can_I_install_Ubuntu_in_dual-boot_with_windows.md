---
title: "How can I install Ubuntu in dual-boot with windows on Asus EeePC 1015PX?"
date: 2011-07-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by MaxReed on 2011-07-20
Hi everybody!
I bought a netbook Asus, an EeePC 1015PX with Win7 Starter. Now I want to install in dual-boot Ubuntu. I created a new partition with Win7 reducing the space of the first partition (the one with Windows). In this moment, for Windows, that space is marked as "not allocated". I tried to install ubuntu by USB disk but he tells me that the space that I have created is unusable.
On the HD there are five partition,one with Win, one for data, one for recovery, one of only 16 Mb that I don't know what is it and what is its function, and the partition created by me.

So, how can I install Ubuntu on my netbook, whereas Ubuntu does not want to use the free space that I created?

Thanks to all and sorry for my english!!

---

### Post by oldfred on 2011-07-20
Did you get a message about windows converting from basic to dynamic partitions? If so it is a big problem. Generally you want to use Windows tools for Windows and Linux tools for Linux. Windows cannot even create a usable partition for Linux unless you are just installing wubi.

Post this from liveCD to see your partitions:

```
sudo fdisk -lu
```

---

### Post by MaxReed on 2011-07-20
Yes, I received a message by Windows that asking me to convert from basic to dyamic partitions, but I denied the request and now I still have basic partition.The new partition is empty and not formatted
As soon as I can I will post what you want.

Do I have to try to reduce the first partition by Gparted during the ubuntu installing process for installing it ? Doesn't this create any problem to Windows?

---

### Post by oldfred on 2011-07-20
I generally suggest with Vista/7 using Windows MMC to shrink the Windows partition. If you have newer versions of gparted or Ubuntu there is no real issue in using gparted to shrink windows. (Any issues go back to when Windows started at sector 2048 & Linux & XP at 63, everyone is using 2048 now). 

If you use gparted, it will run faster if you have run defrag first, so it has to move less data. Leave 30% free space or more in the NTFS partition. If windows does not have lots of free space it starts to run very slow.

I prefer to partition in advance & reboot windows. After a partition size change windows will want to run chkdsk and this will confirm that windows is ok before the Ubuntu install.

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by toor58 on 2011-07-20
in win7 right click on the computer desktop icon and select manage.

when the next window opens select disk management.

you should see (originally) win7 patition, recovery partition, empty data partition, and a small partition for the boot booster.

do not delete your boot booster partition under any circumstances.

you can reduce the win7 partition using windows resizing tool if you wish. 

better and safer for now to delete empty data partiton.

boots ubuntu

install next to win7.

installer will automatically choose the free space (old data partition) and install ubuntu there. 

enjoy

---

### Post by SeijiSensei on 2011-07-20
> **toor58 said:**
> do not delete your boot booster partition under any circumstances.

Why?  I'm pretty sure I deleted it off my daughter's 1201n when I installed Ubuntu.  I occasionally see a message during boot about the "booster," but the machine boots both Win7 and Ubuntu correctly.

---

### Post by MaxReed on 2011-07-20
For oldfred:
I tried what you said but when I try to create a new partition, Gparted (into Ubuntu LiveCD) tells me that isn't possible to create more than four primary partition.So, what can I do? 
I have also seen using Gparted that there is 1 Mb unallocated but Windows does not see it.
If I try to extend Windows partition with Gparted, he tells me that "there may be problems with the boot partition if it is moved". 

For toor58:
I can't and I don't want to use data partition because there are my documents and I want to reduce Windows partition because he don't need of 100 Gb but of only 30 Gb.

---

### Post by oldfred on 2011-07-20
You can only have 4 primary partitions with MBR partitioning. You will have to delete one and convert it to an extended partition that can hold many logical partitions.

You should not plan on directly writing into your Windows system partition. It does not like a lot of writing. Much better to create a shared NTFS partition for read/write from both systems. It can be one of the logical partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

