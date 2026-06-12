---
title: "gparted help"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by guilly on 2007-08-16
I'm just wondering i've created a new partition with gpared under root

now i tried to sign ownership over to my account "user1" by doing sudo chown user1 /dev/sda7 but it still does not give me full access to the partition is there something i'm doing wrong???

thanks

---

### Post by Arthur Archnix on 2007-08-16
Just so I'm clear, are you actually logging into Ubuntu and working as root?

---

### Post by guilly on 2007-08-16
no,

i did a sudo gparted which allowed me to create the partition but i'm loged in as another user

---

### Post by Arthur Archnix on 2007-08-16
Ok, and what was the exact command you ran? Oh, and what's in here:
```
gksudo gedit /etc/fstab
```

---

### Post by guilly on 2007-08-16
i ran sudo gparted created the partition then i did sudo chown jack /dev/sda7 thinking it would give me ownership which it did not. then i did sudo chown jack /media/disk that didnt' work either and fstab has this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5645faad-5438-4d14-bdbf-b607b4fe868d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=90ECADECECADCD32 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=E2A09B64A09B3E4B /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=D2980B79980B5AFD /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=69cc9fac-43c7-484a-98d2-a2cb9ab63ca8 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Arthur Archnix on 2007-08-16
Ok, well, you can't chown sda7 because there isn't one. Same with /media/disk. But let's say /dev/sda2 was the one you wanted to take ownership of, which is found mounted at /media/sda2, the command would be:
```
sudo chown -R user:user /media/sda2
```
my user name is arthur, so in my case it would be:
```
sudo chown -R arthur:arthur /media/sda2
```

---

### Post by guilly on 2007-08-16
i just noticed that as i was posting that there was no sda7 but how come in gparted it comes up as sda7 

are fstab and gparted not comparable?

---

### Post by Arthur Archnix on 2007-08-16
I'd never noticed, but I'd have to guess it's because gparted gives numbers to extended partitions and fstab doesn't. Just a guess. Either way, you go with what you find in /etc/fstab not gparted when doing things like chown, chmod, mount, umount, fdisk, and so forth.

---

### Post by guilly on 2007-08-17
so since sda1 is my primary partition and inside of that i have multiple extended partition I need to give myself ownership of SDA1?

code: chown jack:jack /media/sda1

---

### Post by guilly on 2007-08-17
anybody??

---

### Post by nemequ on 2007-08-17
fstab is *not* a list of all parititions. What file system is on your new (/dev/sda7) partition, and where do you want it mounted?

---

### Post by guilly on 2007-08-17
the file system is ext3 it mounts automatically already in /media/* is fine

i just don't have permissions with my daily user since i had to create the partition with root priviledges? that's my problem

---

### Post by Arthur Archnix on 2007-08-17
> **nemequ said:**
> fstab is *not* a list of all parititions. What file system is on your new (/dev/sda7) partition, and where do you want it mounted?

Ah... I hadn't thought of that. But you're right. Like I said, I was taking a guess. But thanks for pointing that out nemequ. So, how would one look at all partitions without using gparted? I only know of the mount and fstab methods.

EDIT: Wait,so if he rebooted, the partition "unknown" *wouldn't* show up in fstab or the mount command?

---

### Post by nemequ on 2007-08-17
fstab won't necessarily have the partition, even if he rebooted. Ubuntu does some weird stuff with mounting (without changing fstab) that I don't fully grok in order to accommodate USB mass storage device and the like...

Running mount will show you the currently mounted partitions (regardless of whether they're in fstab or not). It will not show unmounted partitions. I don't know why you wouldn't want to use gparted to see the partitions, but fdisk will do it... that's just unnecessarily masochistic, IMHO, though.

Now, guilly, unmount the partition.  Decide where you want it mounted, lets say you choose /media/guilly. `mkdir /media/guilly`, then `gksudo gedit /etc/fstab` and add a line like this:

```
/dev/sha7    /media/guilly    ext3    defaults,uid=1000,gid=1000     0    1
```

Assuming your uid and gid are 1000 (you can check by running `id`). It may work to put your username in there instead, but no promises.

Then, just mount /media/guilly. If you don't want to mount it automatically when your computer starts, just add noauto to the options in fstab.

---

### Post by Arthur Archnix on 2007-08-17
> **nemequ said:**
> fstab won't necessarily have the partition, even if he rebooted. Ubuntu does some weird stuff with mounting (without changing fstab) that I don't fully grok in order to accommodate USB mass storage device and the like...

Running mount will show you the currently mounted partitions (regardless of whether they're in fstab or not). It will not show unmounted partitions. I don't know why you wouldn't want to use gparted to see the partitions, but fdisk will do it... that's just unnecessarily masochistic, IMHO, though.

Thanks Nemequ, just learnin', like guilly. I wish there were a command that could be run from the terminal that would show all partitions... I thought fdisk -l did that. Gonna man fdisk now. Then man mount (ummm... the Linux command :oops: ), since I only tend to read for what I want to know... maybe I missed some good stuff!

---

### Post by guilly on 2007-08-17
> **nemequ said:**
> fstab won't necessarily have the partition, even if he rebooted. Ubuntu does some weird stuff with mounting (without changing fstab) that I don't fully grok in order to accommodate USB mass storage device and the like...

Running mount will show you the currently mounted partitions (regardless of whether they're in fstab or not). It will not show unmounted partitions. I don't know why you wouldn't want to use gparted to see the partitions, but fdisk will do it... that's just unnecessarily masochistic, IMHO, though.

Now, guilly, unmount the partition.  Decide where you want it mounted, lets say you choose /media/guilly. `mkdir /media/guilly`, then `gksudo gedit /etc/fstab` and add a line like this:

```
/dev/sha7    /media/guilly    ext3    defaults,uid=1000,gid=1000     0    1
```

Assuming your uid and gid are 1000 (you can check by running `id`). It may work to put your username in there instead, but no promises.

Then, just mount /media/guilly. If you don't want to mount it automatically when your computer starts, just add noauto to the options in fstab.

Thank you!!! just for my own learning experience, were the steps that i took with gparted correct ? by creating the new partition or would there have been an easier way without having to alter the fstab after to give my user proper permissions?

---

