---
title: "Mounting a &quot;new&quot; ext3 internal harddisk"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by geekchicohio on 2007-05-22
Hey all, I've done some searching around to find a tutorial or explanation for this that I could apply to my situation and get this done on my own, but no luck so far so I'm coming to the community for some help.
I have an internal harddisk that I just used a GPartEd live CD to format to ext3 and I want to mount it permanently so I can use it to store my music.
I'd like to mount it to /media/JukeboxDrive
I've tinkered a bit, to no avail, so hopefully you guys can walk me through doing this.

```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9240    74220268+  83  Linux
/dev/hda2            9241        9729     3927892+  82  Linux swap / Solaris

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7297    58613121   83  Linux

```
it's hdb1 that I'm trying to mount, as you can see.
I've edited fstab and restarted, but no dice.

/etc/fstab shows the following:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bc6d2b4b-7765-4b00-a179-c8705ee5b0a2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
/dev/hdb1       /media/JukeboxDrive     ext3    defaults     0       0
# /dev/hda2
UUID=c1ab0c3b-149e-4e51-af50-d845ef834141 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I'm guessing there are mounting commands I need to, and haven't used in CLI, or else I need the UUID (where would I find this?)
Anyway, any help that you can offer on getting this fixed would be WONDERFUL.
Thanks everyone.

EDIT:
Nearly forgot some other possibly useful info: This is all going down on a brand new install of Feisty.

---

### Post by ruy_lopez on 2007-05-22
If the fstab is configured properly you should be able to just type:

```
sudo mount /media/JukeboxDrive
```

---

### Post by BitTorrentBuddha on 2007-05-22
Your fstab looks right, the only thing I can think of would be to check if the directory /media/JukeboxDrive exists already, I don't believe fstab creates directories. Other than that, fstab should automatically be mounting the drive. The command to manually mount it to check would be:```
sudo mount /dev/hdb1 /media/JukeboxDrive
```

---

### Post by cyberbat on 2007-05-22
You should look at this: [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by geekchicohio on 2007-05-22
Thanks for the quick responses. Here's the latest:
```

heff@heff-desktop:~$ sudo mount /dev/hdb1 /media/JukeboxDrive
Password:
mount: you must specify the filesystem type
heff@heff-desktop:~$ 

```

How would I go about doing that?

---

### Post by ruy_lopez on 2007-05-22
You shouldn't need to specify the device " /dev/hdb1" because the mount command will read all that stuff from the fsstab. Try it without.

```
sudo mount /media/JukeboxDrive
```

Also, make sure you have you done this:
```

sudo mkdir /media/JukeboxDrive
```

---

### Post by BitTorrentBuddha on 2007-05-22
That's odd, specifying filesystem type usually isn't required, but try this:```
sudo mount -t ext3 /dev/hdb1 /media/JukeboxDrive
```

On a side note, typing the command 'man mount' made me giggle a little.

---

### Post by geekchicohio on 2007-05-22
After looking through that tutorial linked by cyberbat I decided to consider starting ALL over.
Glad I did, apparently the drive wasn't formatted properly or wasn't formatted at all. Gparted listed it as "?" as opposed to "ext3" so I'm reformatting and then I oughta be good-to-go.
I'll keep everyone updated.

---

### Post by geekchicohio on 2007-05-22
Mission Accomplished.
Thanks everyone for your help.

---

