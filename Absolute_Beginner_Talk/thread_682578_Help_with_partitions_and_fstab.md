---
title: "Help with partitions and fstab"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by asakurax on 2008-01-30
Well, i had 4 partitions:
sda1 - NTFS - Windows 
sda3 - ext3 - Ubuntu
sda5 - Fat32 -my stuff 
sda6 - NTFS - a 5 gb partition for large files

So now that gutsy supports NTFS, i made sda5 NTFS and merged sda5 and 6
I did all that via Windows
The problem now is that Ubuntu doesn't auto-recognize my new partition and it doesn't auto-mount it.
I guess it's because I need to edit the fstab file, but i don't know how

this is my fstab file now:
```

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d114d10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         545     4377681    7  HPFS/NTFS
/dev/sda2             546        4179    29190105    5  Extended
/dev/sda3            4180        4870     5550457+  83  Linux
/dev/sda5             546        4141    28884838+   7  HPFS/NTFS
/dev/sda6            4142        4179      305203+  82  Linux swap / Solaris
```

Can anyone help me with the editing?

Thanks in advance

Asakurax

---

### Post by jan quark on 2008-01-30
this is a excellent guide on fstab by bodhi.zazen
[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

I will read it now too, I hope you either
and will search a solution for your issue :)

---

### Post by jan quark on 2008-01-30
and I have found this
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

you need ntfs-3g driver to mount the ntfs windows partitions

---

### Post by bumanie on 2008-01-30
If you are using gutsy gibbon, ntfs-3g is included in the kernel and should enable natively. (I believe this is corect).

---

### Post by asakurax on 2008-01-30
Yup, I do have access and write permission to NTFS partitions by default

---

### Post by erfahren on 2008-01-30
@asakurax - what you posted isn't your /etc/fstab but the output of "fdisk -l"

post the output of:
```

cat /etc/fstab

```
also post the output of:
```

blkid

```

---

### Post by asakurax on 2008-01-30
lol
My bad
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                        0  0  
# /dev/sda3
UUID=86c55cb3-65a5-4ab1-826b-05c09c2654c7  /               ext3         defaults,errors=remount-ro      0  1  
# /dev/sda1
UUID=1AA8355CA8353799                      /media/sda1     ntfs         defaults,umask=007,gid=46       0  1  
# /dev/sda5
UUID=60DD-3C63                             /media/sda5     vfat         defaults,utf8,umask=007,gid=46  0  1  
# /dev/sda6
UUID=01C80DBD28876100                      /media/sda6     ntfs         defaults,umask=007,gid=46       0  1  
# /dev/sda7
UUID=b5e5d7ab-3a27-4d08-b4ef-bf0d31b630a6  none            swap         sw                              0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec                0  0  
/dev/scd0                                  /media/cdrom1   udf,iso9660  user,noauto,exec                0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec             0  0  
/dev/sda1                                  /media/sda1     ntfs         defaults                        0  0  
/dev/sda3                                  /media/sda3     ext3         defaults                        0  0  
/dev/sda5                                  /media/sda5     ntfs         nls=iso8859-1,umask=000         0  0  
/dev/sda6                                  /media/sda6     swap         defaults                        0  0  
a

> /dev/sda1: UUID="1AA8355CA8353799" TYPE="ntfs" 
/dev/sda3: UUID="86c55cb3-65a5-4ab1-826b-05c09c2654c7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="CE88D24D88D233A5" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="b5e5d7ab-3a27-4d08-b4ef-bf0d31b630a6"

---

### Post by lut4rp on 2008-01-30
I just had this question in my mind, what happens if you delete your /etc/fstab? I mean, will it regenerate it the next time you boot? or is the pc gone... :)

---

### Post by drowner on 2008-01-30
Those extra 4 lines at the bottom! who added them?

---

### Post by erfahren on 2008-01-30
wow - your fstab is a little messed up - you have your partitions listed twice in there (I'm surprised you were able to boot with it like that)

EDIT: I see you are offline now - I made a statement below and moved it here (as follows):
Actually, if it were me I think I'd replace the whole fstab with what I have here (after backing it up) and reboot. What I have there is correct - I double checked it.


try this - first back your current one up
```

sudo cp /etc/fstab /etc/fstab_back

```
then unmount the /dev/sda5 
```

sudo umount /dev/sda5

```
and replace the line - with the /dev/sda5 line I have below - (you ultimately want your fstab to look something like this without the partitions being listed twice) 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0 
# /dev/sda1
UUID=1AA8355CA8353799 /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda3
UUID=86c55cb3-65a5-4ab1-826b-05c09c2654c7 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=CE88D24D88D233A5 /media/sda5 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda6
UUID=b5e5d7ab-3a27-4d08-b4ef-bf0d31b630a6 none swap sw 0 0
# EXTERNAL MEDIA DEVICES
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0 
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0 
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0


```
remove the four lines at the bottom of your current one (and also that "a" )
then remount all
```

sudo mount -a

```

---

### Post by drowner on 2008-01-30
eidt: damn - beaten to it!

---

### Post by erfahren on 2008-01-30
oh, if you do decide to just replace it - just have the directories: /media/sda1 and /media/sda5 already created. (they should already be there) 

you can delete the two directories /media/sda3 and /media/sda6

note: I put some links to information on fstab and permissions in this post on another thread:
[http://ubuntuforums.org/showpost.php?p=4229726&postcount=9](http://ubuntuforums.org/showpost.php?p=4229726&postcount=9)

---

