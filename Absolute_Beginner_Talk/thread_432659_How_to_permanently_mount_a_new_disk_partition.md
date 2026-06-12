---
title: "How to permanently mount a new disk partition"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by RedBoot on 2007-05-04
Not exactly a noobe, but this issue makes me feel like one :confused: 
Looked at a lot of posts and resources, but still sketchy on how to permanently mount a new NTFS partition (created in Vista). I am looking for the exact line(s) to add to fstab.

Here is info so far:
```
cat fstab
...snip...
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d7c6a666-9ccd-4f14-9ddc-7d03c5a8c41b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4F18D68C65FBF8F8 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=15696205-872d-45ac-af31-0fd2d7584bae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Here is current partition setup; It's the /dev/sda5 I want to get at.
```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5343    42916501    7  HPFS/NTFS
/dev/sda2            5344        9167    30716280   83  Linux
/dev/sda3            9168        9550     3076447+  82  Linux swap / Solaris
/dev/sda4            9551       19458    79578112    f  W95 Ext'd (LBA)
/dev/sda5            9551       12610    24576000    7  HPFS/NTFS
```

Assuming I'm wanting to use sda5, I  created a mount point "/media/sda5" and made it look like the one for sda1:
 > ls -dl /media/sda*
dr-xr-x--- 1 root plugdev 8192 2007-05-02 22:10 /media/sda1
dr-xr-x--- 2 root plugdev 4096 2007-05-03 15:44 /media/sda5

BTW, I don't know if the fact that Vista made this a logical partition inside of sda4 makes any difference. 
Appreciate any help.

---

### Post by Skrynesaver on 2007-05-04
What you need to do is 
```

sudo vol_id -u /dev/sda5

```copy the output of this and add the following line to /etc/fstab
```

#/dev/sda5
UUID=<output_of_vol_id_command> /media/sda5  ntfs defaults,nls=utf8,umask=007,gid=46 0       1
```then run 
```

sudo mount -a
```

Partitioning requires that there be only four primary partitions, one of these can be an extended partition((s|h)da4) and all logical partitions are created within this.

---

### Post by RedBoot on 2007-05-04
Skrynesaver,

That's just the info I needed. It's up and working great!

Thanks much! Ubuntu Rocks!

---

### Post by nolan- on 2007-05-05
Fantastic, thanks this helped me a lot.

:guitar:

---

### Post by Creak on 2007-12-02
Exactly what I needed to know too! Thanks a lot!
Why isn't it a bit more friendly to add a hard disk drive into Linux... gParted is great, but it still doesn't do labeling, doesn't add entries to the fstab, doesn't give uuid, stuff like that that would be very nice after all...

Well, wait and see! Thanks again!

---

### Post by rare HERO on 2008-02-29
Thanks for that.

---

### Post by tarehart on 2008-03-05
I'm in a slightly different situation, and I'm hoping somebody can throw me a specific line to add to fstab.

When installing ubuntu, I set up a Data partition formatted to fat32. I immediately had a change of heart and used gparted to reformat it as ext3. As a consequence, it did not mount automatically on startup and when I mount manually, it's read only.

Based on this thread, I changed its line in fstab to this:
(originally it had a different UUID and the filesystem was fat32)

```
UUID=7c3e1a92-e964-4296-bbad-8ec5aba0ea45  /media/Data     ext3    defaults 0       1
```

Now it shows up under /media/Data, but it's still read only. Also, it is not given a drive icon or included in "Computer" under the places menu. Thoughts?

---

### Post by Oldsoldier2003 on 2008-03-05
> **tarehart said:**
> I'm in a slightly different situation, and I'm hoping somebody can throw me a specific line to add to fstab.

When installing ubuntu, I set up a Data partition formatted to fat32. I immediately had a change of heart and used gparted to reformat it as ext3. As a consequence, it did not mount automatically on startup and when I mount manually, it's read only.

Based on this thread, I changed its line in fstab to this:
(originally it had a different UUID and the filesystem was fat32)

```
UUID=7c3e1a92-e964-4296-bbad-8ec5aba0ea45  /media/Data     ext3    defaults 0       1
```

Now it shows up under /media/Data, but it's still read only. Also, it is not given a drive icon or included in "Computer" under the places menu. Thoughts?

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)


try this:
```
UUID=7c3e1a92-e964-4296-bbad-8ec5aba0ea45  /media/Data  ext3 auto,users,rw 0 0
```

---

### Post by tarehart on 2008-03-05
Ah, excellent. With that new line, Data is getting proper treatment as a partition again. Unfortunately, I still lack write permissions. I'll study up on that link you gave me and try to figure it out.

This was progress, though, so thanks!

---

### Post by rare HERO on 2008-03-05
> **tarehart said:**
> Ah, excellent. With that new line, Data is getting proper treatment as a partition again. Unfortunately, I still lack write permissions. I'll study up on that link you gave me and try to figure it out.

This was progress, though, so thanks!

Should be as easy as using SUDO to give yourself permissions. Try this:

```
$ gksudo nautilus
```

Navigate to your folder '/media/Data'; right click; properties; tab over to properties; make your user the owner and give yourself all the access you need.

In case this doesn't make sense check out this link:
[http://www.techotopia.com/index.php/Browsing_My_Computer%2C_Files_and_Folders_on_the_Ubuntu_Desktop]("http://www.techotopia.com/index.php/Browsing_My_Computer%2C_Files_and_Folders_on_the_Ubuntu_Desktop")

Alternatively you can do this, where user is your username:
```
sudo chown user '/media/Data'
```

More info on this thread:
[http://ubuntuforums.org/showthread.php?t=67657]("http://ubuntuforums.org/showthread.php?t=67657")

and this page:
[http://www.psychocats.net/ubuntu/permissions]("http://www.psychocats.net/ubuntu/permissions")

---

### Post by tarehart on 2008-03-06
Your first option worked perfectly, thanks!

---

