---
title: "USB external hard drive"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2008-03-31
i have a 500 gigabyte external usb hard drive. i already formated the drive with GPARTED in ext3. 

when i connect the drive to my PC, and try to copy something to it, it says i do not have the permissions to do so.

can anyone help me?

i am a noob in linux so any detailed help is appreciatted.

---

### Post by Michael.Godawski on 2008-03-31
```
sudo chown -R usr:usr CU

sudo chmod -R 755 CU
```

Change usr to your username and CU to the path to the drive.

Use this code to change permission on folders and file. 

You might perhaps want to mount the external drive automatically at start up already with the right permissions set. To do this you need to edit your fstab file as described here.

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by cmaranhao on 2008-03-31
when i tried that commands in terminal it said this:

maranhao@maranhao-desktop:~$ sudo chown -R usr:usr /dev/sdb
Password:
chown: `usr:usr': invalid user


what should i do now?

(in the mean time i will take a look in your link but the point is to make a backup of my data to the USB hard drive, format my pc and restore everything afterwards.. then give the hard drive to its owner)

---

### Post by Michael.Godawski on 2008-03-31
You have to enter your username instead of usr:usr. So for instance if your username is john the correct command would be:
```

sudo chown -R john:john /path/to/drive
```

---

### Post by cmaranhao on 2008-03-31
yes, lol

like i said, i am a noob but that was really dumb on my part.

anyway, here it goes:

maranhao@maranhao-desktop:~$ sudo chown -R maranhao /dev/sdb
maranhao@maranhao-desktop:~$ sudo chmod -R 755 /dev/sdb
maranhao@maranhao-desktop:~$ 


but i still can't copy anything to the USB drive. it still says i do not have the permissions.

---

### Post by Michael.Godawski on 2008-03-31
You have typed this:
```

sudo chown -R maranhao /dev/sdb
```

but it must be that:

```

sudo chown -R** maranhao:maranhao** /dev/sdb
```

---

### Post by cmaranhao on 2008-03-31
ok, i hadn't notice that detail.

i did it right this time?

maranhao@maranhao-desktop:~$ sudo chown -R maranhao:maranhao /dev/sdb
maranhao@maranhao-desktop:~$ sudo chmod -R 755 /dev/sdb
maranhao@maranhao-desktop:~$ 


but when i drag and drop the files it still says i don't have the permissions.

---

### Post by Michael.Godawski on 2008-03-31
This time it is correct.

Please post the results of these commands. They will give us some additional info about your drives.

```
sudo fdisk -l
```
```

cat /etc/fstab
```

---

### Post by cmaranhao on 2008-03-31
> maranhao@maranhao-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12289693+  83  Linux
/dev/hda2            1531        2550     8193150   83  Linux
/dev/hda3            2551        9729    57665317+   5  Extended
/dev/hda5            2551        9729    57665286   83  Linux

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1             132       24792   198089482+   5  Extended
/dev/hdb5             132       24792   198089451   83  Linux

Disk /dev/hdd: 17.3 GB, 17340000256 bytes
255 heads, 63 sectors/track, 2108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1         261     2096451   82  Linux swap / Solaris
/dev/hdd2             262        2108    14836027+   5  Extended
/dev/hdd5             262        2108    14835996   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+  83  Linux




> maranhao@maranhao-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=56a34c95-594c-4ec0-a1ba-1103a80ba7ba /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=36891008-e4d1-47f8-a0cd-f087200d6b73 /home/backup ext3    defaults        0       2
# /dev/hdb5
UUID=a2552123-ef3c-43a3-b9f0-ec6ac93142e9 /home/multimedia ext3    defaults        0       2
# /dev/hdd5
UUID=94f53955-0eb6-48ae-9e76-bb2def17eee5 /home/incoming ext3    defaults        0       2
# /dev/hdd1
UUID=577ab0ba-a609-4ffb-9231-fac464941ebb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /home/downloads ext3 defaults 0 2
maranhao@maranhao-desktop:~$ 


help?

---

### Post by Inxsible on 2008-03-31
I dont think the command is correct. The path should not be /dev/sdb1

It should be the path to the mount point of that drive. What is the mount point of the drive?if you dont know post the output of this command. It will list the drive and the mount point```
df -h
```

---

### Post by cmaranhao on 2008-03-31
and how should i do that?

---

### Post by Inxsible on 2008-03-31
> **cmaranhao said:**
> and how should i do that? Like I told you in the previous post

---

### Post by cmaranhao on 2008-03-31
sorry. i missed your post.

and it now worked.. ot should be like this:

> maranhao@maranhao-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             7.7G  3.9G  3.5G  53% /
varrun                506M  132K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  124K  506M   1% /proc/bus/usb
udev                  506M  124K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/hda5              55G   47G  4.6G  92% /home/backup
/dev/hdb5             186G  147G   31G  83% /home/multimedia
/dev/hdd5              14G   10G  3.3G  76% /home/incoming
/dev/hda1              12G  158M   11G   2% /home/downloads
/dev/sdb1             459G  199M  435G   1% /media/disk
maranhao@maranhao-desktop:~$ sudo chown -R maranhao:maranhao /media/disk
maranhao@maranhao-desktop:~$ sudo chmod -R 755 /media/disk
maranhao@maranhao-desktop:~$ 

many thanks for your help and your effort when i was being a dumb.

regards

---

### Post by Inxsible on 2008-03-31
so then did you use the chown and chmod command on the /media/disk mount point ?

So you are all set then eh ?

---

### Post by cmaranhao on 2008-03-31
looks like i will need more help. 

i tried to copy a folder by dragging and dropping (its a hard drive actually) and it placed an icon (with only 14 bytes) of that folder in the USB drive .

when i tried to copy a single file, it copied with no problems but the folder is giving trouble.

i need further help to copy my contents.

---

### Post by Inxsible on 2008-03-31
> **cmaranhao said:**
> looks like i will need more help. 

i tried to copy a folder by dragging and dropping (its a hard drive actually) and it placed an icon (with only 14 bytes) of that folder in the USB drive .

when i tried to copy a single file, it copied with no problems but the folder is giving trouble.

i need further help to copy my contents.That's strange !

If you can copy a file, folders shouldn't be a problem. Its definitely not a permissions issue anymore.

---

### Post by cmaranhao on 2008-03-31
one more thing, i can only copy by dragging and dropping. if i click with the right button and then press copy and paste in the hard drive, the paste option is greyed out and i can't paste the contents.

only by dragging and dropping.. 

what about a command to copy the contents using terminal? how should it be?

can you give me an example so i can try it here?

---

### Post by cmaranhao on 2008-03-31
i tried this command to copy in terminal

 cp -r /home/downloads /media/disk

downloads is a folder and i want to put it in the USB drive.

it gave me this:

> maranhao@maranhao-desktop:~$ cp -r /home/downloads /media/disk
cp: cannot access `/home/downloads/lost+found': Permission denied
maranhao@maranhao-desktop:~$ 

---

### Post by Inxsible on 2008-03-31
have you executed this command yet ?

```
sudo chown -R maranhao:maranhao /media/disk
```

---

### Post by cmaranhao on 2008-03-31
yes, i've done that command.. i needed 3 tried but i done it like you said.

but now i tried something else.. i opened the folder and inside it i have other folders. i dragged and dropped and it started copying.

looks like i can't drag and drop the hard drive itself (it is mounted as a folder inside home).

---

