---
title: "Mounting a drive into a directory"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-12-31
Hello all,
I've added a new hard drive to my system. I was able to format it using the partition manager, but I can't figure out how to mount it. Can someone help me out? My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8e23a7fa-0d7e-4b34-a4ef-64b6ec4926d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4be63f13-b368-43ea-829e-daeaac8fe631 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


I'd like to mount this drive into a directory called shared, which is where all shared files will go. I need to be able to configure Samba to let me share the directory with other machines on my network.

---

### Post by taurus on 2006-12-31
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by gantww on 2006-12-31
I'm sorry for being so slow, but I still don't quite get it.

I formatted the partition as an ext3 partition. According to the partition manager, it is hdb. So, can you help me out on creating a line in the file that will mount it (all the examples were NTFS).

Thanks,
Will

---

### Post by taurus on 2006-12-31
Okay, here goes.  Open a terminal to edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.
```
/dev/hdb1   /media/shared   ext3   defaults   0   1
```
Save it and create a new mount point and mount it.

```
sudo mkdir /media/shared
sudo mount -a
sudo chmod -R 777 /media/shared  <-- change permissions so you can write to it...
df -h  <-- you should see your /dev/hdb1 mounted on /media/shared now
```

---

### Post by gantww on 2006-12-31
Sweet!

Will it mount now after I reboot?

---

### Post by taurus on 2006-12-31
It will mount to /media/shared everytime you boot your machine.  ;)

---

### Post by gantww on 2006-12-31
Most excellent. Now I just need to to set up my samba shares in there and I'm all set.

---

### Post by Anakist on 2006-12-31
> **taurus said:**
> 
and add this line to the end of it.
```
/dev/hdb1   /media/shared   ext3   defaults   0   1
```

Can you translate this into edgy? I put that in and got errors.

I have:
/dev/hdc
mounting onto
/media/main
it is
ntfs

What defaults do I use? Thanks.

James

---

