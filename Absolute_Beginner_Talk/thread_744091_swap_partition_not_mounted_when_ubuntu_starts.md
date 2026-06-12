---
title: "swap partition not mounted when ubuntu starts"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-04-03
I'm not sure what happened, but when I boot ubuntu the swap partition isn't mounted. Under the System Monitor it shows 0 of 0 bytes being used. If I open the Gnome Partition Editor I can then turn the swap on and system monitor then shows my 1.5 gb swap.  Does anybody know how to get the swap on by default?

---

### Post by Diabolis on 2008-04-03
Did you mess with your fstab file? If so, thats were you can fix it. My swap entry is this one:

```

/etc/fstab

/dev/sda3 none            swap    sw              0       0
```

If you moved/resized the partition, it's uuid changed and you have to updated. You can see which is it by issuing the command **blkid**.

---

### Post by mali2297 on 2008-04-03
Perhaps you need to edit the file /etc/fstab. Open it with
```

gksu gedit /etc/fstab

```
Locate the line that concerns swap and change into something like
```

/dev/hda7           none            swap    sw            0       0

```
I have my swap partition on /dev/hda7, you need to check where yours is and modify the above line accordingly.

---

### Post by neurostu on 2008-04-03
I did resize my swap. I shrunk it down from 4 gb to 1.5

So do I just change the UUID in the fstab file to match what the UUID is when I type blkid?

---

### Post by Diabolis on 2008-04-03
yes

---

### Post by neurostu on 2008-04-03
or do I just remove the UUID tab?

---

### Post by mali2297 on 2008-04-03
> **neurostu said:**
> I did resize my swap. I shrunk it down from 4 gb to 1.5

So do I just change the UUID in the fstab file to match what the UUID is when I type blkid?

Yes, or you could just replace the UUID stuff in fstab with something like /dev/hda7.

---

### Post by Diabolis on 2008-04-03
you can either just replace the uuid with the new one or use the **/dev/sdx#** route.

I think its better to use uuid because it only changes when changes are made to the partitions and the routes like **/dev/sdx#** change depending on the number of drives that you have plugged in and on the order in which they are plugged in.

---

### Post by neurostu on 2008-04-03
```
 blkid 
```
returns:
```

/dev/sda1: UUID="FE50F02F50EFEBF9" LABEL="HDD" TYPE="ntfs" 
/dev/sda2: UUID="F8C8924CC8920950" LABEL="Synapse" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="cf13d167-0ab8-418a-be5d-1b21e4b0ed58" 
/dev/sda4: UUID="3b3ca04d-1a77-4582-a376-a037cf7ace29" SEC_TYPE="ext2" TYPE="ext3" 

```

So i edited  /etc/fstab to look like 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=3b3ca04d-1a77-4582-a376-a037cf7ace29 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=FE50F02F50EFEBF9 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=F8C8924CC8920950 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3 
UUID=3b3ca04d-1a77-4582-a376-a037cf7ace29 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Does this look correct? I really dont' want to mess us my fstab file

---

### Post by fela on 2008-04-03
isn't 1.5gb swap a bit huge? how much RAM do you have?

---

### Post by Diabolis on 2008-04-03
Nop, you used the wrong uuid. The uuid for your swap partition is: **cf13d167-0ab8-418a-be5d-1b21e4b0ed58**

You can notice that is wrong because now you have duplicate uuids in your fstab file.

---

### Post by mali2297 on 2008-04-03
> **neurostu said:**
> ```
 blkid 
```
returns:
```

/dev/sda1: UUID="FE50F02F50EFEBF9" LABEL="HDD" TYPE="ntfs" 
/dev/sda2: UUID="F8C8924CC8920950" LABEL="Synapse" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="cf13d167-0ab8-418a-be5d-1b21e4b0ed58" 
/dev/sda4: UUID="3b3ca04d-1a77-4582-a376-a037cf7ace29" SEC_TYPE="ext2" TYPE="ext3" 

```

So i edited  /etc/fstab to look like 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=3b3ca04d-1a77-4582-a376-a037cf7ace29 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=FE50F02F50EFEBF9 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=F8C8924CC8920950 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3 
UUID=3b3ca04d-1a77-4582-a376-a037cf7ace29 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Does this look correct? I really dont' want to mess us my fstab file

You seem to have copied the wrong line.

EDIT: I'm just an echo. :rolleyes: You will manage without me.

---

### Post by neurostu on 2008-04-03
THANK YOU mali2297 & Diabolis!!!

You really helped me out and learned a lot.

> 
isn't 1.5gb swap a bit huge? how much RAM do you have?

That depends on what you're trying to do. For the average user yes, I have 2gb of ram installed but i also do a lot of data analysis on my laptop. I open data sets in matlab that are >800mb and having the swap large helps  keep my computer going.

---

### Post by Diabolis on 2008-04-03
I'm glad you got it fixed.

---

### Post by neurostu on 2008-04-08
Ok so I just rebooted and the swap wasn't on. I had to open the partition manager to re-enable the swap.
What is going on here?

---

### Post by neurostu on 2008-04-08
So when I ran:
```

cat /etc/fstab

```
I noticed the following line
```

# /dev/sda3 
UUID=cf13d167-0ab8-418a-be5d-1b21e4b0ed58none            swap    sw              0       0

```

There wasn't a space between the UUID and none, so I put the space in there and hopefully that will fix the problem. If it doesn't when I reboot I will post back.

---

### Post by Diabolis on 2008-04-08
Yeah probably not having that space between the uuid and "none" is the cause of the problem.

---

