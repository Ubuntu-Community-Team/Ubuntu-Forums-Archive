---
title: "Need help with linux partition please"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by jeremycollins08 on 2008-04-07
I'm trying to install dual boot for a friend, and he has a compaq presario computer. 
We get to the prepare partitions screen, and we are choosing the guided method where you select the percent to give to ubuntu. Its step 4 in the install. 

When we press the continue button after setting the partition settings i want, it asks to confirm that you have to write the changes to disk. I hit ok, and it began...but it stopped with an error that reads:

```
An error occurred while writing the changes to the storage devices.

The resize operation is aborted.
```

Then, it shows my two partitions: NTFS and FAT32.

Can someone please help me (us)? We've spent much time on it, and he's bought new ram and everything for this to work but we dont know what to do anymore. 

Also...is it possible to do a remote desktop from the live cd?

Thanks!!!

---

### Post by bodhi.zazen on 2008-04-07
Hard to know for sure.

Try first booting to windows and defragmenting the current partitions.

Then boot ubuntu, make sure the partitions are not mounted and try to resize them with gparted. Then re-try the installer.

---

### Post by benerivo on 2008-04-07
Well it failed in resizing your existing partition which I would guess is not all that unusual as it can be a difficult process. I think you might be able to give a helping hand and also try it another way. If the machine still has windows on it, you should go in and run the defragmant program twice. Also, I would try to repartition the drive from the live cd using the gparted partition manager program (if gparted isn't in the menu then you can install it using synaptic). If you haven't used gparted before then it is a program that can delete, create and resize partitions. It can be used to create the partition setup you want to have when you install linux. If this actually works (!), then you should choose the manual option when it gets to the partition point during the installation process.

---

### Post by jeremycollins08 on 2008-04-07
ok...how can i figure out what to make the partitions? i've only did the guided option with mine, and once i did have to delete the partitions linux made through gparted, so i have a little experience with gparted. But what partitions do i make? His partitions are NTFS and FAT32. I didnt have fat32, just ntfs, and i made a swap. but i dont know what to do with his.

---

### Post by bodhi.zazen on 2008-04-07
You need a minimum of two partitions, swap and / (root)

Size swap = RAM X 2, max 1 Gb ; swap = RAM on laptops.

Put the rest in / (min 5 Gb )

You can choose to make a separate /home or data partition.

See these links :

partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by benerivo on 2008-04-07
Read [this]("http://www.psychocats.net/ubuntu/partitioning"), and then if you need any more info just ask.

---

### Post by jeremycollins08 on 2008-04-07
Thanks for the documents! Just one question...with an ntfs and fat32 partition, do i create just an ext and a home in gparted or what?

---

### Post by bodhi.zazen on 2008-04-07
Resize the ntfs / fat partitions, then make new ones (swap and ext3) in the free space.

DO NOT FORMAT the ntfs or fat partitions.

---

### Post by jeremycollins08 on 2008-04-07
ok, thanks! i will have to try to resize them and make the new ones.

---

### Post by jeremycollins08 on 2008-04-07
How much do i resize the ntfs and the fat32 partitions? i have 80gb disk and like 732 mb of ram.

---

### Post by bodhi.zazen on 2008-04-07
LOL

How much free space do you have in your partitions ?

You can not reduce the size of a partition my more then the available free space.

Ideal sizes : Swap - 1 Gb Root - 5 Gb

---

### Post by benerivo on 2008-04-07
I would resize to create a partition of 1GB for swap, and another partition of at least 4GB (ext3) for ubuntu. The partitions on the drive can be in any order what so ever.

I would only say, don't reduce the existing partitions so much that there is hardly any room left on them for more data. Look at [this]("http://www.linux-user.de/ausgabe/2006/06/034-distribits/gparted.png") picture. hda6 has hardly any free space left!

---

### Post by jeremycollins08 on 2008-04-07
Ok, one question...will it hurt to resize the fat32 partition all the way to as far as it can go? Because i do not have 1 gb even if i resize it all the way, its like 950mb. It stops over half way, and it yellow...

---

### Post by bodhi.zazen on 2008-04-07
You will be "OK" with a smaller swap. 512 Mb would be fine.

---

### Post by jeremycollins08 on 2008-04-07
ok, i did that, its at 959mb, but on the manual partitioner, the swap partition is not selectable, only one, and thats the ext 3 one. also, do i make the ext 3 extended or primary partition?

---

### Post by benerivo on 2008-04-07
Ideally it would just be a primary partition, so you would have your drive divided in to four sections of unequal size (ntfs, fat32, swap, ext3). If you have this, you are good to go.

---

### Post by jeremycollins08 on 2008-04-07
i chose manual partitioning, and selected the root/ ext 3 partition, but it won't let me select the swap partition???

---

### Post by bodhi.zazen on 2008-04-07
swap is automatic, even with manual partitioning.

---

### Post by jeremycollins08 on 2008-04-07
oh, but when i click on forward, it wont let me...it says 


```

No root file system is defined.

Please correct this from the partitioning menu.
```

Do i have to swap on the swap partition? I tried this once but got the same thing, and i just unswapped the swap partition and it still didnt work.

---

### Post by Xappe on 2008-04-07
make the choice to edit the partition, and choose the mountpoint / for it...

---

### Post by jeremycollins08 on 2008-04-07
ok, thanks! i will try that.

---

### Post by jeremycollins08 on 2008-04-07
Thanks people! Everything is installed and we are just trying to work with the VNC that is installed. 

It wont connect.

---

