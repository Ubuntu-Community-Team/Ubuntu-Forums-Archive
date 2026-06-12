---
title: "AutoMounting harddisk..."
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by taekr on 2007-12-19
I have been searching for a way to do it.. But confused and not sure..  

Here is my situation. 

I just reinstalled Ubuntu 7.10 with partitions... 

80GB Harddisk is now 

/root - 10GB
/home - 25GB
/swap - 2GB
the remaining is formated as ext3 (it's partitioned)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        4255    24410767+  83  Linux
/dev/sda3            4256        9483    41993910   83  Linux
/dev/sda4            9484        9729     1975995   82  Linux swap / Solaris

Because I just formated the remaining, Ubuntu doesn't mount it automatically. I can mount it manually. then I noticed that the ownership of it is Root not me. So What I want is to have it mounted automatically and the ownership is me not root. 

the following is from fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2601aa6f-9981-4064-9b84-f685fc6fd873 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=26d45fbe-ec80-4e22-8afe-306f3ea40962 /home           ext3    defaults        0       2
# /dev/sda4
UUID=04fc6261-5c31-426a-a19d-7696b7b16c73 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

As you can see, it doesn't mount /dev/sda3 (the remaining) 

According to what I found, 

I need to add 

/dev/sda3 /media/mountpoint ext3 defaults,errors=remount-ro 0 1

But I'm very confused.  this format doesn't match the ones in fstab. 
Their format is 

# bal.. bla..
UUID= Bla.. bla.. bla.. 

Like that..    Hm.. 

Can you help me???   

Two things need to be done. 

Automount the remaining 
the ownership of the remaining is me not root. 

Cheers,

---

### Post by taekr on 2007-12-19
Is it a hard question??  ^ ^;;

---

### Post by Cypher on 2007-12-19
The UUID is the new way of referring to /dev/sdaX like you have, you can get the UUID value by doing
```

vol_id /dev/sda3

```
and entering that value in the /etc/fstab file. But what you have there should work, you can confirm that by doing
```

sudo mount -a

```
This will attempt to mount all the partitions listed in the FSTAB file. If it works, you should see the /media/mountpoint directory show up in the "DF" command.

Once that works, you can create a new directory in the /media/mountpoint as Root and then assign ownership to any user you wish..

---

### Post by taekr on 2007-12-19
Thanks for the advice. 

But ^ ^;; could you give me more step-by-step instructions?? 

I edited fstab by adding # /dev/sda3 and the line below.  (without understanding what is defaults and 0 mean..  just copied the format of /dev/sda2.  Is it ok?)

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2601aa6f-9981-4064-9b84-f685fc6fd873 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=26d45fbe-ec80-4e22-8afe-306f3ea40962 /home           ext3    defaults        0       2
# /dev/sda3
UUID=76f38a04-936f-49a3-9f28-e4a0aea43fb5 /media/disk	  ext3    defaults        0       2  
# /dev/sda4
UUID=04fc6261-5c31-426a-a19d-7696b7b16c73 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



Now, sda3 is automatically mounted. Then, I don't know what to do??

Btw, am I right about adding the lines?

---

### Post by rkd on 2007-12-19
You got the new lines in fstab right.

The rest of Cypher's instructions simply mean you should use a chown command to make the mount point be owned by the user who you want to own the files on the disk mounted there.

If your login name is taekr, that command would be:

```
sudo chown taekr /media/disk
```

Substitute your actual login name for taekr in the command.

I don't know whether you can make that change while /dev/sda3 is mounted.  I think it would be safest to do it thus:

```
sudo umount /media/disk
sudo chown taekr /media/disk
sudo mount -a
```

---

### Post by A$h X on 2007-12-19
Just install pysdm from synaptic. It allows you full control over all partitions. Trust me, I was struggling alot until this wonderful app came along.

---

