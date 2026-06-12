---
title: "help please"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-02-28
i just started the installation . i have 80g HD two partitions c and d . each 40G.
i got to the point called : prepare partitions and when when i chose to do it manually i see : 
1) dev/hdc1 in ntfs 38 g
2) dev/hdc2 extended 28.83 g. under this i see another thing called hdc5 in fat32 also same size( same partition)
3) i did something and it created me another partition called: unallocated 9.41G

i want to install it on my D drive i dont know what to chose .
after this i have to "prepare mount points" ( i dont have any idea what  it means ) something about chose a place for swap and a place for root. 
if you can explain me what to do . thanks allot!

---

### Post by mikewhatever on 2007-02-28
You first HDD is dev/hda, second dev/hdb and so on. The number is added to designate partitions. Thus dev/hda1 is the first partition on the first HDD, dev/hda2 is the second. The mount points should be set up like this: '/' for root, 'swap' for swap, no quotes.
It would be alot easier if you'd posted a screenshot.

---

### Post by fanny on 2007-02-28
i cant post a screen shot im through xp now..

---

### Post by kingcharles1666 on 2007-02-28
read this first:
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/non-debian-partitioning.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/non-debian-partitioning.html)

and this
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/module-details.html#partman](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/module-details.html#partman)

---

### Post by mikewhatever on 2007-02-28
In XP, can you go to Start->Control Panel->Administrative Tools->Computer Managment->Disk Management, maximize the window and take a screenshot. Alt+PrntScr will take a snap shot, and then you can save it in Paint, and post here.

---

### Post by ajgreeny on 2007-02-28
I am assuming that your computer has windows XP already on it, now in hdc1.   Just be carefull that the 9.41Gb partition isn't a backup of all your original software on the hard disk; a lot of computer manufacturers don't give you a full Windows XP install CD, but just a restore CD which will put windows and all the software originally on the computer (perhaps in this hidden partition) back to exactly as it was when you bought it.  If you get rid of that you will not be able to restore windows and other software if you need to.

If however you are sure that you did make this partition by whatever you did and that it wasn't rthere before you tried to install ubuntu, then you can simply and safely delete it using gparted on the ubuntu live CD, as well as the other 28.83Gb partition.  Now when you install, for ease just let the installer use the unallocated space (the 9.41 + 28.83Gb now unallocated).  It will then put ubuntu into hdc2, and swap, which is an absolute necessity, in hdc5.  Don't worry about all this, it will all become a lot clearer as you get to know linux and ubuntu.

Welcome to the gang, and good luck.

---

### Post by mikewhatever on 2007-02-28
I think Windows is on dev/hdc1 because it is NTFS and primary.

---

### Post by fanny on 2007-02-28
sorry i cant show i you the disk managment the file is too big  think

---

### Post by fanny on 2007-02-28
here is my disk

---

### Post by mikewhatever on 2007-02-28
If you want, upload it to [http://www.filefactory.com/](http://www.filefactory.com/) and post the link here.
I think the best thing you can do is to set up Ubuntu on the unallocated space. I needed, you can resize the dev/hdc2 a bit more, but it is not necessary. Choose manual partitions setup and create two partitions in the unallocated space, root and swap, mount them as / and swap, and format the root as etx3. Make swap about 500 MB and give the rest to root. If you are not sure, select automatic partitioning option.
Mount the Windows partition as /media/hdc1. Do not format it.

---

### Post by fanny on 2007-02-28
my problem is when i get to "prepare mount points" i see hdc1 and hdc5 if i change it to HDC2 it doesnt show anything.

---

### Post by mikewhatever on 2007-02-28
> **fanny said:**
> my problem is when i get to "prepare mount points" i see hdc1 and hdc5 if i change it to HDC2 it doesnt show anything.
Do not change anything. I forgot about the second partition, so here it is:
Partition  mount point
root            /
swap         swap
hdc1         /media/hdc1
hdc5         /media/hdc5

---

### Post by fanny on 2007-02-28
if i will install on hdc1 it means it will install it on c: (xp) (cause i dont wont it on c) any way before i try again . i see hdc2  it is fat32"logical"? what does it mean . cause no matter what i do i choose swap or root( "\") it gives me the next message:"a partition is assigned to more then one points!" 
what should i do? do i supposed to write something somewhere?
anyway maybe i can do something in xp before to make a usual partition?

---

### Post by mikewhatever on 2007-02-28
> **fanny said:**
> if i will install on hdc1 it means it will install it on c: (xp) (cause i dont wont it on c) any way before i try again . i see hdc2  it is fat32"logical"? what does it mean . cause no matter what i do i choose swap or root( "\") it gives me the next message:"a partition is assigned to more then one points!" 
what should i do? do i supposed to write something somewhere?
anyway maybe i can do something in xp before to make a usual partition?
Do not install on hdc1 or on hdc5 and do not format them. All you do is mount them by making the mount points. hdc2 is logical as opposed to hdc1 that is primary. It is another topic and does not affect the installation. You have to install Ubuntu in the unallocated space only. To do that, you need to create two new partitions in that unallocated space, root and swap. Root is mounted as /, and swap as swap.

---

### Post by fanny on 2007-03-01
what does it mean 'mount points' ? i f i chose to mount in hdc1 it will install it on hdc1?

---

### Post by mikewhatever on 2007-03-01
> **fanny said:**
> what does it mean 'mount points' ? i f i chose to mount in hdc1 it will install it on hdc1?

No, mounting and installation are two different things. You mount a partition to get access to its files from Ubuntu, that's it. Read more on mounting here [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)
Now, go to this site [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) and look at the pictures. At the picture 'step 6 of 7' choose 'manually edit partition table', no need to resize because you've done that already. Now, your partition table will open. 
hdc1 is your NTFS Windows partition
hdc2 is extended, and can have many more partitions like hdc5
hdc5 is FAT32 logical partition
and then there is all the unallocated space.

Right click on the unallocated space and create two partitions in that space, one root, the other swap. Swap should be about 500 MB, the rest of space is for root. It does not matter if the partitions you create are primary or logical.
Now, you have to mount all of the partitions:
the root partition is mounted as /
the swap partition is mounted as swap
the Windows NTFS is mounted as /media/hda1
the FAT32 is mounted as /media/hda5

Choose to format the root and the swap, and NOT the other two.

---

