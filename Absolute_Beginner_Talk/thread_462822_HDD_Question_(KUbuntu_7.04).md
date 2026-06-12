---
title: "HDD Question (KUbuntu 7.04)"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by L1nux01D on 2007-06-03
Hello everyone!Have a question:How to format unlocated partition to ext3?I have a partition above 50GB and I can't use it.I loaded from Ubuntu LiveCD and from Disk Manager formated.It's now ext3 filesystem,but I still can't use it.Please tell me how to format this part,and how to make it usefull?

---

### Post by AtrejuT on 2007-06-03
So do you already have a running Ubuntu system and want to use this partition? Or where do you want to use it?

If you want to use it in an already installed Ubuntu system you have to mount it somewhere. Therefore you need to know the name of the disk (e.g. /dev/hda3 or such, it is displayed in gparted).

There is a lot of information about this e.g. here:
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
and here:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by L1nux01D on 2007-06-03
I know how to mount patritions.I need to make unlocated Part into ext3...When I mount this part,it says,that I don't have permission.I want to be owner of this part.

---

### Post by AtrejuT on 2007-06-03
So did you do the following (just to understand correctly)?
- In gparted make a partition for the unallocated part (and apply)
- in gparted, right click the partition, select format to - ext3 (and apply)
- either added an entry to fstab or mount it manually using sudo to the folder you want. (mount always requires sudo)

can you tell me exactly where it goes wrong/what the error message is?

---

### Post by indytim on 2007-06-03
I'm not sure how Ubuntu is currently configured (I'm on Kubuntu).  First I would suggest installing GParted from the repository if you don't have it installed at the present.  After GParted is installed, go ahead and launch it.  From there you will get a graphical map of your HD.  If it shows (I think 4 max) primary partitions, you are in what I call "partition lock".  This means you will not be able to do anything with your unallocated space (except grow an existing adjoining partition).  If this applies, the only way out is to delete a partition (ouch).  Again, if this all applies, after you have deleted the partition, then, using GParted create an extended partition.  Once this is done, then WITHIN this extended partition, create additional partitions.

Not sure if this addresses your problem, hope it helps.

IndyTim

---

### Post by L1nux01D on 2007-06-03
- I made those 3 steps from LiveC
- Reboot to KUbuntu
- Mount
- Try to write something at this partition
- Don't have enough rights,Im' not owner.....

---

### Post by L1nux01D on 2007-06-03
2 indytim VERY BIG THANKS!!I installed GParted,and now formatting,will see what going to be...

---

### Post by L1nux01D on 2007-06-03
No.......Still can't

LOOK AT THE BOTTOM OF THE WINDOW

[[IMG]http://aycu18.webshots.com/image/17377/2004922065028286393_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004922065028286393)



I tried to to extract something to this part,but still same result

[[IMG]http://aycu40.webshots.com/image/15719/2004924991160656693_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004924991160656693)

---

### Post by AtrejuT on 2007-06-03
try something like 
```

sudo chmod 666 /dev/hda5

```
and can you also post the output of
```

sudo fdisk -l

```

---

### Post by L1nux01D on 2007-06-03
Yeah,thanks.Just found this operation.Thanks everyone,I solved this problem.If anyone will have same problem just follow this link    

[http://ubuntuforums.org/showthread.php?t=459047&highlight=ntfs+write](http://ubuntuforums.org/showthread.php?t=459047&highlight=ntfs+write)

---

