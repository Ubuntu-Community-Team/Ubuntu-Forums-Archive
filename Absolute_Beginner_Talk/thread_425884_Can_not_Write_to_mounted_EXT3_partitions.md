---
title: "Can not Write to mounted EXT3 partitions"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-04-28
Ubuntu 7.04, 64 bit.
Made a test file with Gedit.
Saving to an old FAT32 warns - " could not create backup, save anyway". Saves.
But unable to save to any of the new EXT3 partitions. They are mounted.
Do I have to mount them as /document or /***** to be able to write ?

I think that documentation should include some explanation on Linux file systems.

---

### Post by aysiu on 2007-04-28
One of these should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by dptxp on 2007-04-28
Thanks.
What I gather is that my partitions, The FAT32 and EXT3 are mounted
 but wrongly mounted.
The correct way is to mount them as some directory in root.
Either during installation , or by editing later.

Can you tell me something about the error I get on boot :

[COLOR="Navy"]There is offset between boot sector and its backuo.
[/COLOR]
There is a table of values and at the end I get,
[COLOR="Navy"]Not Automatically Fixing This.
[/COLOR]

Mine is dual boot with XP.

---

### Post by dptxp on 2007-04-30
I reinstalled, I wanted to avoid editing fstab, made sure that the partitions were mounted, this time the ext3 partitions as /data1 and /data2 and fat32 partitions as /windows and /data0.

I still can not access the ext3 partitions, I am not allowed to save, the message is sort of - "you do not have permission to ..".

fstab lists the ext3  partitions as

...... ext3      defaults       0         2


I edited  2 to 0, made defaults,user  , followed up by mount -a, no effect.

Ubuntu 6.04 used to mount differently. This is Feisty. Do I have no choice but to
edit the /etc/fstab as suggested ?

---

### Post by darkrose on 2007-04-30
Can you paste your /etc/fstab here?

---

### Post by obbe on 2007-04-30
to enable the ext3 writing try to make *sudo chmod 777 /folder/disk* in a terminal.
note: usually disks are mounted in /media/ ):P

---

### Post by dptxp on 2007-04-30
Here are the contents of /etc/fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=bc812a17-e091-4df6-a8a3-74723cffe0c3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda9
UUID=045A-BCA1  /data0          vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=cbb6441a-80d5-4ae4-8b37-0664a48b06dc /data1          ext3    defaults        0       2
# /dev/hda6
UUID=968470eb-85ba-4ec0-8bb0-4f32b0198724 /data2          ext3    defaults        0       2
# /dev/hda1
UUID=84B8-09C9  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=f1b9dbc3-6049-427e-92b2-f16f4d944850 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


Tried sudo chmod 777 /folder/disk as per other suggestion.
Result - No file or directory found.

And when I save to the fat32 partitions, it says - "Unable to create backup, save anyway ?". It saves when I say yes.

---

### Post by dptxp on 2007-04-30
help !! help !! help !!

---

### Post by darkrose on 2007-04-30
try running this in a terminal:

sudo chgrp -R  YOURUSERNAME /data1

raplacing YOURUSERNAME with, err, your user name. Then:

sudo chmod g+rwx /data1

and see if you can save to the directory /data1

---

### Post by Drakkor on 2007-04-30
Try this:

---

### Post by dptxp on 2007-04-30
> **darkrose said:**
> try running this in a terminal:

sudo chgrp -R  YOURUSERNAME /data1

raplacing YOURUSERNAME with, err, your user name. Then:

sudo chmod g+rwx /data1

and see if you can save to the directory /data1


It worked !!!!!
1) What was wrong ? Why did I not have rw permission as default ?
2) Can you also please tell me why I get that message "Unable to make back up, save anyway"
for fat32 ? Is there a way to correct it ?

---

### Post by darkrose on 2007-04-30
> **dptxp said:**
> It worked !!!!!
1) What was wrong ? Why did I not have rw permission as default ?
2) Can you also please tell me why I get that message "Unable to make back up, save anyway"
for fat32 ? Is there a way to correct it ?

Excellent!
The partitions were mounted in the root of the filesystem (/) so had rw permissions for the root user only. They would most likely have to be mounted in /media - e.g. /media/data1 - to give a regular user rw permissions by default.

The first command changed the group ownership of the /data1 directory to your users group, second cammand just ensured you could read and write to the directory.

You should be able to run both of those cammands for /data0 and /data2 (if you haven't already to clear up their permissions.

As for the message from FAT, it should go away when you change it's owner ship and permissions.

---

### Post by dptxp on 2007-04-30
Thanks a lot. I am using Linux for first time. Learning.

BTW Yesterday I had logged at terminal as root user, that had not worked, maybe login as root
user would have given access.

I have done so with data2 too, I am going to do so with data0 (it is the fat32 one).

Couple of more questions:- 

1) I have used myusername for the commands. Will other users
be able to access the partitions ? Do I have to do anything to enable access to others ?

2) I have a problem of getting this message after boot and grub-
" Offset in back up of boot sector"
Then I see the offset values and then the message -
" Not fixing this automatically"

I get this irrespective of the partition I choose as /, or the Ubuntu version 6.10 or 7.04.
I use 64 bit, pc configuration at signature.

Why do I get this ? Can it be corrected ? Can it create any problems ?

---

### Post by darkrose on 2007-04-30
To let other users access the directories, just run:
useradd -G yourusername newusername

Which will add them to the group that owns the directories.  Or when you set up a new account, just be sure to add them to that group.

Re: "Offset in backup of boot sector"
is this refering to the particular partition, or does it come up before checking/mounting filesystems?
It's likely to be more annoying than dangerous, but might as well see if we can clear it up.

---

### Post by dptxp on 2007-05-01
Surprising , all console (non gui) info I used to see do not show up any more. Only Kernel Loading ......
The offset error message gone, all message gone.
Hopefully the fault is gone. Ubuntu still runs.

Ubuntu loads fast now.

When I try the rw enable the fat32 partition (I had not formatted it, it had data), on first command I get

[COLOR="Navy"]chgrp: changing group of '/data0 ' Operation not permitted.
[/COLOR]
The line shown here is the last line, the list has similar lines, only file names (and paths) added after /data0.

---

