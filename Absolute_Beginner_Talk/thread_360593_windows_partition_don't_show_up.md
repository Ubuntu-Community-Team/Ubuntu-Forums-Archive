---
title: "windows partition don't show up"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-13
can windows partitions show up in Computer?
i want to access my mp3's and documents :)

---

### Post by ComplexNumber on 2007-02-13
> **panti19 said:**
> can windows partitions show up in Computer?
i want to access my mp3's and documents :)
it should be called something like X GB Volume hda1 (eg 11.7 GB Volume hda1).

---

### Post by taurus on 2007-02-13
You need to mount it before you can access it.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by dannyboy79 on 2007-02-13
> **ComplexNumber said:**
> it should be called something like X GB Volume hda1 (eg 11.7 GB Volume hda1).

huh?

you need to mount the drive to a folder you create. it depends if this drive is on the network, is this a drive in a dual boot system, is this a partition within the same drive, what is the fs, fat32 or ntfs? check out this guide for mounting a ntfs or fat32 drive and or partition that is within the same computer that you have ubuntu installed on. if it's a usb drive, it should of popped up on your desktop.


we can maybe help you, post the output frmo these commands that you would type into a terminal. (the comman line in linux)

sudo cat /etc/fstab


sudo fdisk -l


Note: sudo will ask you for a password, this will be the same password you set up for your username. 

here is a guide for mounting shares from a windows computer over the network:
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

here is a guide for mounting ntfs or fat32 drives within the same computer.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)


make sure that if you can't figure it out from the guides I posted, that when you repost back here, you provide the info I asked for otherwise it's hard to help you.

---

### Post by dannyboy79 on 2007-02-13
> **taurus said:**
> You need to mount it before you can access it.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

huh taurus, you beat me to it!!!!

---

### Post by taurus on 2007-02-13
> **dannyboy79 said:**
> 
sudo cat /etc/fstab

Just so you know, you don't need to use sudo to view /etc/fstab.

```
cat /etc/fstab
```

---

### Post by panti19 on 2007-02-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=97f9939d-d372-4397-9760-f807c786cd27 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e9a6c661-089c-417a-91b9-3bb4a90eefa7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


and after sudo fdisk -l


Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2747    22065246    7  HPFS/NTFS
/dev/hda2   *        2748        4775    16289910   83  Linux
/dev/hda3            4776        4866      730957+   5  Extended
/dev/hda5            4776        4866      730926   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/hdb5               2        9729    78140128+   7  HPFS/NTFS

Disk /dev/sda: 1007 MB, 1007681536 bytes
31 heads, 62 sectors/track, 1024 cylinders
Units = cylinders of 1922 * 512 = 984064 bytes

   Device Boot      Start         End      Blocks   Id  System

---

### Post by taurus on 2007-02-13
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdb5   /media/hdb5   ntfs   nls=utf8,umask=0222   0   0
```
Save the changes and create two new mount points and mount them.

```
sudo mkdir /media/hda1 /media/hdb5
sudo mount -a
df -h
```

---

### Post by dannyboy79 on 2007-02-13
> **taurus said:**
> Just so you know, you don't need to use sudo to view /etc/fstab.

```
cat /etc/fstab
```

good call, I merely put that because I am so used to actually editing the fstab file instead of just viewing it. I suppose we need to be clear so that we don't mess up newbies. Thanks for pointing this out for others as I was already aware of this

---

### Post by ComplexNumber on 2007-02-13
> **dannyboy79 said:**
> huh?

i was assuming that he was asking what it was called (ie its not called windows).

as it happens, when i first installed ubuntu, the windows partition showed up in Computer. i didn't need to change the fstab file.
all thats necessary is the ntfs packages to be installed.


**panti19**
when you're ready, and if you want to have write access to the windows partition, [this]("http://gnomefiles.org/app.php/ntfs-config") application can do the trick.

---

### Post by dannyboy79 on 2007-02-13
panti19, just so you are aware you don't have to do it exactly as taurus is suggesting. Those are only suggestions. you can create the folder wherever you like and you can name them whatever you like. for example, you stated that those partitions had music on them. well you could create a music folder within your /home/username directory. so then your fstab entry would be either

/dev/hda1   /home/username/music    ntfs   nls=utf8,umask=0222   0   0

or


/dev/hdb5   /home/username/music    ntfs   nls=utf8,umask=0222   0   0

and then you would have to create the folder just like he stated above but with the new name. also make sure you chown the folder if you want it owned by you and not by root. that would be 

sudo chown username:username /home/username/music. (note: username is YOUR username. this then makes the mount point owned by your user as well as you users group which is the same as the user's name) then if you want to also be able to write to this directory, you'll want to look at this tutorial here: [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

the support for ntfs writing has come along way and was just relaeased under RC1 recently. good luck

---

### Post by dannyboy79 on 2007-02-13
> **ComplexNumber said:**
>  i was assuming that he was asking what it was called (ie its not called windows).

as it happens, when i fisrst installed ubuntu, the windows partition showed up in Computer. i didn't need to change the fstab file. 

after re-reading the original post I suppose I can sort of see your point but at first I couldn't figure out what the heck you meant.

---

### Post by ComplexNumber on 2007-02-13
**dannyboy79**
concentrate on helping panti19 from now on.

---

### Post by dannyboy79 on 2007-02-13
> **ComplexNumber said:**
> **dannyboy79**
concentrate on helping panti19 from now on.


excuse me?? do you think you are my dad? just so you are aware I am reporting this.

---

### Post by muguwmp67 on 2007-02-13
> **ComplexNumber said:**
> 
as it happens, when i first installed ubuntu, the windows partition showed up in Computer. i didn't need to change the fstab file.
all thats necessary is the ntfs packages to be installed.

I figured this one out.  When you use manual partitioning during the install, ubuntu fstabs your windows partitions.  Automatic partitioning does not do this.

A different issue from mounting them after install, but maybe the information will help someone in the future.

---

### Post by taurus on 2007-02-13
> **dannyboy79 said:**
> excuse me?? do you think you are my dad? just so you are aware I am reporting this.

Just calm down and stick to the topic of this thread, okay.

---

### Post by dannyboy79 on 2007-02-13
> **taurus said:**
> Just calm down, okay.

taurus, I am calm. I have to be honest, this is not the first time that I have seen an admin try to "flex" his administrative muscles and I think that this kind of thing is just unacceptable. I have been doing nothing but helping this person so I don't know what his post was all about. I have done what I said I would do and I'll see what gets done about it.

---

### Post by panti19 on 2007-02-13
thanks guys for all the help.. i don't know what i did, but when i restarted the system it found my 2 hard drives. :)

---

### Post by dannyboy79 on 2007-02-13
panti19, I am glad you got it. are you saying that when you retarted the 2 other partitions were in your fstab?

---

### Post by taurus on 2007-02-13
> **dannyboy79 said:**
> taurus, I am calm. I have to be honest, this is not the first time that I have seen an admin try to "flex" his administrative muscles and I think that this kind of thing is just unacceptable. I have been doing nothing but helping this person so I don't know what his post was all about. I have done what I said I would do and I'll see what gets done about it.

dannyboy79,

I don't think ComplexNumber was trying to flex his administrative muscles or anything.  He was trying to keep the discussions on the topic of the thread, helping panti19 to mount his/her ntfs partitions.  

Now that everybody is calm and relax, everything is all good again, right!  ;)

---

### Post by dannyboy79 on 2007-02-13
> **taurus said:**
> dannyboy79,

I don't think ComplexNumber was trying to flex his administrative muscles or anything.  He was trying to keep the discussions on the topic of the thread, helping panti19 to mount his/her ntfs partitions.  

Now that everybody is calm and relax, everything is all good again, right!  ;)

if he wanted the topic to stay on track than he could've said that instead of what he did say and also the use of bold letters is an indication of his "tone" and or "attitude". as long as admin's don't boss people around barking orders and telling them what to do than yes, everything is alright. :)

---

