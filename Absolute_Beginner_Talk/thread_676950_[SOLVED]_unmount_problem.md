---
title: "[SOLVED] unmount problem"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by srikrishnan on 2008-01-24
Hi All,

I have three windows partitions in my hard disk. When I open my system in Ubuntu those partitions are as default in unmount mode. Everytime i need to mount those manually.

I hope there is an option to set all those partitions in mount mode.

Can anybody help me to solve this problem?

Regards,
Srikrishnan

---

### Post by erginemr on 2008-01-24
Can you please post your "/etc/fstab" file here?
And the output of the command "sudo fdisk -l"?

---

### Post by srikrishnan on 2008-01-24
Hi erginemr,

Here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd7
UUID=e0e8acb7-e42c-411f-9a34-e56b995190a5 /               ext2    defaults,errors=remount-ro 0       1
# /dev/hdd2
UUID=140C8F0D0C8EE8D6 /media/hdd2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdd3
UUID=C49C6FAA9C6F95A8 /media/hdd3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdd4
UUID=2C989BAE989B7554 /media/hdd4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdd6
UUID=B480-806D  /media/hdd6     vfat    defaults,umask=007,gid=46 0       1
# /dev/hdd5
UUID=ac4ddc7d-f243-4157-b973-f8aef1c311f7 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

regards,
Srikrishnan

---

### Post by PmDematagoda on 2008-01-24
Could you please post the output of:-
```
blkid
```

---

### Post by kshane on 2008-01-24
> **srikrishnan said:**
> Hi All,

I have three windows partitions in my hard disk. When I open my system in Ubuntu those partitions are as default in unmount mode. Everytime i need to mount those manually.

I hope there is an option to set all those partitions in mount mode.

Can anybody help me to solve this problem?

Regards,
Srikrishnan

Can you post the output from:

```
cat /etc/fstab
```
...and
```
blkid
```

Kevin

---

### Post by srikrishnan on 2008-01-24
Hi Kshane/PmDematagoda/erginemr,

Thanks for your responses,

srikrishnan@srikrishnan-desktop:~$ blkid
/dev/hdd2: UUID="140C8F0D0C8EE8D6" LABEL="disk[hdd2]" TYPE="ntfs" 
/dev/hdd3: UUID="4284A86484A85BE3" LABEL="New Volume" TYPE="ntfs" 
/dev/hdd4: UUID="983801193800F7D0" LABEL="disk[hdd4]" TYPE="ntfs" 
/dev/hdd5: TYPE="swap" UUID="ac4ddc7d-f243-4157-b973-f8aef1c311f7" 
/dev/hdd6: UUID="5C54322954320674" LABEL="NEW VOLUME" TYPE="ntfs" 
/dev/hdd7: UUID="e0e8acb7-e42c-411f-9a34-e56b995190a5" TYPE="ext2" 

Regards,
Srikrishnan

---

### Post by PmDematagoda on 2008-01-24
Post the output of:-
```
sudo mount -a
```

---

### Post by srikrishnan on 2008-01-24
Hi,

Below is the result:

srikrishnan@srikrishnan-desktop:~$ sudo mount -a
[sudo] password for srikrishnan:
Failed to access '/dev/disk/by-uuid/C49C6FAA9C6F95A8': No such file or directory
Failed to access '/dev/disk/by-uuid/2C989BAE989B7554': No such file or directory
mount: special device /dev/disk/by-uuid/B480-806D does not exist
srikrishnan@srikrishnan-desktop:~$

---

### Post by PmDematagoda on 2008-01-24
Open the fstab file for editing using:-
```
sudo gedit /etc/fstab
```
and edit the file to make it look like this:-
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdd7
UUID=e0e8acb7-e42c-411f-9a34-e56b995190a5 / ext2 defaults,errors=remount-ro 0 1
# /dev/hdd2
[COLOR="Red"]**/dev/hdd2**[/COLOR] /media/hdd2 ntfs defaults,umask=007,gid=46 0 1
# /dev/hdd3
**[COLOR="Red"]/dev/hdd3[/COLOR]** /media/hdd3 ntfs defaults,umask=007,gid=46 0 1
# /dev/hdd4
[COLOR="Red"]**/dev/hdd4**[/COLOR] /media/hdd4 ntfs defaults,umask=007,gid=46 0 1
# /dev/hdd6
UUID=B480-806D /media/hdd6 vfat defaults,umask=007,gid=46 0 1
# /dev/hdd5
UUID=ac4ddc7d-f243-4157-b973-f8aef1c311f7 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
```

After the changes are done, save the file and execute:-
```
sudo mount -a
```
post any errors you get.

---

### Post by srikrishnan on 2008-01-24
Hi,

Thanks for your help

Following is the new message I received:

srikrishnan@srikrishnan-desktop:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/B480-806D does not exist

Also, what is for the following lines:

# /dev/hdd6
UUID=B480-806D /media/hdd6 vfat defaults,umask=007,gid=46 0 1

we dont need to change this?

Regards,
Srikrishnan

---

### Post by PmDematagoda on 2008-01-24
Yes, I think doing that can fix that final problem, so the file should look like this:-
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdd7
UUID=e0e8acb7-e42c-411f-9a34-e56b995190a5 / ext2 defaults,errors=remount-ro 0 1
# /dev/hdd2
/dev/hdd2 /media/hdd2 ntfs defaults,umask=007,gid=46 0 1
# /dev/hdd3
/dev/hdd3 /media/hdd3 ntfs defaults,umask=007,gid=46 0 1
# /dev/hdd4
/dev/hdd4 /media/hdd4 ntfs defaults,umask=007,gid=46 0 1
# /dev/hdd6
[COLOR="Red"]**/dev/hdd6**[/COLOR] /media/hdd6 vfat defaults,umask=007,gid=46 0 1
# /dev/hdd5
UUID=ac4ddc7d-f243-4157-b973-f8aef1c311f7 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
```

That should fix your problem once and for all.

---

### Post by srikrishnan on 2008-01-24
Hi,


Thanks a lot for your continuous help to solve my problem.

Actually, my fourth windows partition also is in NTFS file system. But in Linux it shows as "vfat".

After I have changed it, now everything works perfect.

Thank you very much.

Regards,
Srikrishnan

---

### Post by srikrishnan on 2008-01-24
Hi,

One More Question,

I have seen in many of yours reply there is a column for "Thanks" and "Thanked". 

But I don't know how to add my thanks to my repliers.

Regards,
Srikrishnan

---

### Post by thelatinist on 2008-01-24
> **srikrishnan said:**
> Hi,

One More Question,

I have seen in many of yours reply there is a column for "Thanks" and "Thanked". 

But I don't know how to add my thanks to my repliers.

Regards,
Srikrishnan

Just click the little blue ribbon and gold star at the bottom of any post you found helpful to thank the poster.

---

