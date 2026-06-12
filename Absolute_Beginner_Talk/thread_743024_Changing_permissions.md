---
title: "Changing permissions"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Mildredd on 2008-04-02
As with the other threads I've started I've looked at others and am getting nowhere. I've been using Ubuntu for...this is the second day.

I've been following some instructions on other threads but now i can't even unmount it seems. Now I don't have permission and the command sudo unmount isn't recognized as a command.

I created a partition as FAT separate from my OS partition so I can save documents separately and securely and be able to access them through Windows. Problem being, i don't have permissions on anything. 

Help would be appreciated, however, i'll need things explained in extremely simple terms. =/

Here's a screen of the properties from a folder I've made in my FAT partition

[IMG]http://i35.photobucket.com/albums/d195/M-D-K/Screenshot-untitledfolder1Propertie.png[/IMG]

---

### Post by c-ron on 2008-04-02
The command to unmount is:

```
sudo umount /dev/(driveandpartition)
```

Note that there's only one N in umount.

You need to define permissions for the mountable partitions in /etc/fstab

See this for a detailed explanation of the process:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by ferdostar on 2008-04-02
I suppose you have a dual-boot with Windows partition. So I think that you can [_**check this**_]("http://www.psychocats.net/ubuntu/mountwindows#fat32").

---

### Post by Mildredd on 2008-04-02
Hi, I tried reading that link previously Ferdostar but as i'm new it means nothing to me. Doesn't seem to be written in a newb friendly way. 

Would you be able to type a command I can copy and paste?

I run a vista/ubuntu dual boot using separate HD's. Ubuntu was installed in it's own partition and i made another partition as FAT so i can save documents there and also access them in windows. I want to mount the FAT partition and have permissions on it.

---

### Post by ferdostar on 2008-04-02
Can you post you the content of your /etc/fstab file please.
EDIT: and post the outut of ```
sudo fdisk -l
```

---

### Post by bumanie on 2008-04-02
I am not totally at ease with this subject, however, I think you are missing the point, that just because you have added an extra partition, that this doesn't mean that ubuntu will immediately recognise it and be able to use it. You will have to edit /etc/fstab at least and if you want data to save there upon clicking 'save', you will have to make a directory path to the new partition. It is quite involved and I am not proficient enough to guide you. You may be interested to know that ubuntu since 7.10 can read/write to ntfs and thus you don' really need a FAT32 partition.

---

### Post by Mildredd on 2008-04-02
I typed /etc/fstab and it says permission denied

fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4edb4dd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48642   390708224    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005653e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6527    52428096   83  Linux
/dev/sdb2            6528       40808   275362132+   b  W95 FAT32
/dev/sdb3           40809       41853     8386560+  82  Linux swap / Solaris

sdb2 is the partition i planned to use for storing documents etc which is why i want permissions. otherwise i don't see the point in using it.


Bumanie, my reason for this thread is because i want to have permission on files and documents i'm saving to a certain dedicated partition. I know it doesn't recognize them immediately which is why i'm asking for help.

---

### Post by ferdostar on 2008-04-02
> **Mildredd said:**
> I typed /etc/fstab and it says permission denied

```
cat /etc/fstab
```

and post the output

---

### Post by Mildredd on 2008-04-02
I found my fstab in recent documents, but the command worked too.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=cb637dca-e8f1-4985-9ac8-e6e32ba06622 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=47F1-333C  /media/sdb2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb3
UUID=a0fccd4e-24bd-4b26-abfd-7f7f76336217 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by dannyboy79 on 2008-04-02
nevermind

it's look like you have it right within your fstab, you just need to chown the directory.

that would be 

sudo chown username:groupname /folder/

example

say I just created a folder within /usr/ and I named it test. and my name and group name is frank.

this would be the command

sudo chown frank:frank /usr/test

also, paste the results of this

ls -la /media/

I am guessing it's because fat32 filesystems don't have owners or groups. Mine is the same way. ls -la /media for me returns this:

drwxrwx---  7 root   plugdev 32768 1969-12-31 18:00 fat32

my folder within /media/ is named fat32, that's a 300gb hard drive that's formatted as fat32. when i tried to chown it recursively, I got operation not permitted even when using sudo. they remain owned by root and group plugdev. Just use sudo to paste stuff in it.

---

### Post by Mildredd on 2008-04-02
> **Mildredd said:**
> I typed /etc/fstab and it says permission denied

fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4edb4dd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48642   390708224    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005653e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6527    52428096   83  Linux
/dev/sdb2            6528       40808   275362132+   b  W95 FAT32
/dev/sdb3           40809       41853     8386560+  82  Linux swap / Solaris

sdb2 is the partition i planned to use for storing documents etc which is why i want permissions. otherwise i don't see the point in using it.


Posted it above separately

So if i wanted permission on the FAT partition I would type

sudo chown myusername:mygroupname /media/sdb2 ??

---

### Post by ferdostar on 2008-04-02
> **Mildredd said:**
> I found my fstab in recent documents, but the command worked too.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=cb637dca-e8f1-4985-9ac8-e6e32ba06622 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=47F1-333C  /media/sdb2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb3
UUID=a0fccd4e-24bd-4b26-abfd-7f7f76336217 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Not sure but try this one:
1) Make a backup of /etc/fstab
2) In terminal:```
sudo gedit /etc/fstab
```
3) Than edit the line from ```
# /dev/sdb2
UUID=47F1-333C  /media/sdb2     vfat    defaults,utf8,umask=007,gid=46 0       1
``` to ```
# /dev/sdb2
UUID=47F1-333C  /media/sdb2     vfat    defaults,utf8,[COLOR="Red"]umask=000 0 0[/COLOR],gid=46 0       1
```
Save and exit
4) ```
sudo mount -a
```

---

### Post by Mildredd on 2008-04-02
says line 8 in fstab is bad

---

### Post by ferdostar on 2008-04-02
> **Mildredd said:**
> says line 8 in fstab is bad

:( 

Try to change to```
# /dev/sdb2
UUID=47F1-333C  /media/sdb2 vfat rw,auto,umask=000 0 0
```

---

### Post by Mildredd on 2008-04-02
still the same, bad line

permissions in the properties of the partition say plugdev. should that not be root?? like the other partitions? How can I change that back? I must've changed it following some advice in another 'permissions' thread.

[img]http://i35.photobucket.com/albums/d195/M-D-K/Screenshot-untitledfolder1Propertie.png[/img]

also, the partition seems to have mounted itself again.

---

### Post by dannyboy79 on 2008-04-02
I have a fat32 hard drive. my fstab looks like this

# /dev/hdb1
UUID=81B8-2F2C  /media/fat32    vfat    defaults,utf8,umask=007,gid=46 0       1

and when I issue the mount command from the cli, it shows this:

/dev/hdb1 on /media/fat32 type vfat (rw,utf8,umask=007,gid=46)

I can write a file to a folder that I created on that drive by merely issuing

touch test.txt

in theory you should be able to write to it despite it being owned by root because you should be in the plugdev group. what does this command show?

groups

only entered when you're logged in as yourself.

---

### Post by Mildredd on 2008-04-02
> **dannyboy79 said:**
> please re-read my post.

total 40
drwxr-xr-x  5 root root     4096 2008-04-02 16:57 .
drwxr-xr-x 23 root root     4096 2008-04-02 14:47 ..
lrwxrwxrwx  1 root root        6 2008-03-31 21:45 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2008-03-31 21:45 cdrom0
-rw-r--r--  1 root root       69 2008-04-02 16:57 .hal-mtab
-rw-------  1 root root        0 2008-04-02 16:57 .hal-mtab-lock
drwxrwxrwx  1 root root     8192 2008-04-02 16:59 OS
drwxrwx---  3 root plugdev 16384 1970-01-01 01:00 sdb2

i replied to your post about the command for chown. can you check it?

'sudo chown myusername:mygroupname /media/sdb2 ??'

UPDATE

i typed sudo chown mdk:mdk /media/sdb2 and got 'chown: changing ownership of `/media/sdb2': Operation not permitted'

---

### Post by dannyboy79 on 2008-04-02
i know, that's what I was saying. I don't think a mounted fat32 partition folders can be chowned. Did you see my post above, I had edited it apparently a little too late since you already quoted me.

---

