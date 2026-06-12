---
title: "Help with partitioning drives"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by coderboi on 2006-07-07
Hi

I've never administered a linux machine and I am having some trouble with partitioning.  I have Dapper installed ok but I realized that the partition was smaller than I wanted.  So I used gparted and took some space away from my windows partion and created a new partition.  Then I went to System > Disks and clicked the partition tab.  I created a mount point /mnt/hda4 and enabled the partition.  Is that all I have to do?  Is there anything else that is needed?

Thanks

cb

---

### Post by Denis on 2006-07-07
The steps you have taken are right. However, mounting the partition with the "Disks" application will only mount it once. This means that if you reboot, you will have to mount the partition again. 

To mount a partition at bootup, you should adjust /etc/fstab (as a root user): ```
sudo gedit /etc/fstab
```

Add a line to this text file, like the following: 
```

/dev/hda4  /mnt/hda4  ext3  defaults  0  0
```

Now your /dev/hda4 hard disk will be mounted at /mnt/hda4 at bootup (assuming the filesystem is ext3). 

If you can now use the directory (place files in it), it is set up correctly. If you can't use it, you have to check the permisions of the directory. Right click on the directory and chose the permissions tab. If the owner is "root", make sure everything is checked for Owner, Group and Others. Read, write and execute should definitely be enabled for "others" (since you are "other" than root). To fix this, run the following in the terminal: ```
sudo chmod 777 /mnt/hda4
``` (Or run nautilus as a root and check all the boxes in the permission tab)

---

### Post by coderboi on 2006-07-07
> **Denis said:**
> The steps you have taken are right. However, mounting the partition with the "Disks" application will only mount it once. This means that if you reboot, you will have to mount the partition again. 

To mount a partition at bootup, you should adjust /etc/fstab (as a root user): ```
sudo gedit /etc/fstab
```

Add a line to this text file, like the following: 
```

/dev/hda4  /mnt/hda4  ext3  defaults  0  0
```

Now your /dev/hda4 hard disk will be mounted at /mnt/hda4 at bootup (assuming the filesystem is ext3). 

If you can now use the directory (place files in it), it is set up correctly. If you can't use it, you have to check the permisions of the directory. Right click on the directory and chose the permissions tab. If the owner is "root", make sure everything is checked for Owner, Group and Others. Read, write and execute should definitely be enabled for "others" (since you are "other" than root). To fix this, run the following in the terminal: ```
sudo chmod 777 /mnt/hda4
``` (Or run nautilus as a root and check all the boxes in the permission tab)


Thanks for the info.  One question, is it possible to just make the original partition I have for ubuntu larger instead of creating a 2nd partion and mounting it?  I tried to do it in gparted off the livecd and wasnt able to do it.  All I can do is create a new partition.

thanks!

cb

---

### Post by Denis on 2006-07-08
You can't change the beginning of an ext3 partition in Gparted (I think this isn't possible at all). So the only thing you can do is make the ext3 partition larger (extend to the right side). 

A workaround would be to copy that partition to another disk, delete the original and make a new partition that has the desired size. Then copy the data to the new partition. 

I'm not sure this is worth the effort for you. Maybe you can use the new partition you've created to mount a specific directory (something like /home/username/images). In that case, make sure to copy over the data of course. You won't really notice that this directory is on a different partition that way.

---

