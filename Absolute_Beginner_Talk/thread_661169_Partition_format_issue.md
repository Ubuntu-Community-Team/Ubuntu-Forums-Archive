---
title: "Partition format issue"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by ckamc on 2008-01-07
I have three linux partitions

/
swap
free space

when I try and access the free space ext3 I am unable to create folders as it tells me I do not have permission/ownership over the space

I just want to use the free space to have all my media/documents on, any suggestions? format to ext2? reiserfs?

using Gparted

---

### Post by reckless2k2 on 2008-01-07
i owuld use gparted to make the free space ext3 to be consistent with ubuntu. once you reboot, it should/will detect it and yadda.....yadda.

---

### Post by tech9 on 2008-01-07
> **ckamc said:**
> I have three linux partitions

/
swap
free space

when I try and access the free space ext3 I am unable to create folders as it tells me I do not have permission/ownership over the space

I just want to use the free space to have all my media/documents on, any suggestions? format to ext2? reiserfs?

using Gparted

yes, use gparted to format the free space as ext2 or ext3
you should be able to save your files to your new location

---

### Post by ckamc on 2008-01-07
I just restarted and got this message

> Log of fsck -C -R -A -a 
Mon Jan  7 16:12:37 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=44a59d6b-f39e-4804-ad82-d9bac089d912' 
fsck died with exit status 8

---

### Post by tech9 on 2008-01-07
> **ckamc said:**
> I just restarted and got this message you could try booting up wit your liveCD and input the correct UUID in your /etc/fstab

---

### Post by plucky on 2008-01-07
ckamc,

The **uuid** in **/etc/fstab** has changed because you changed the partition.The system will continue to boot to the login screen if you **Ctrl D** and allow it to continue.
Then ```
cat /etc/fstab
``` which will show you the **UUID** that the system is expecting to see.
Open a terminal **Applications >Accessories > Terminal** and input ```
blkid
``` and this will give you the current **UUID** for all your partitions.Then you need to edit your /etc/fstab file to reflect the **UUID** of the new partition
```
gksudo gedit /etc/fstab
``` and copy and paste the new **uuid** into the /etc/fstab file and reboot.

Good luck.

---

### Post by ckamc on 2008-01-07
> cat: /ect/fstab: No such file or directory


i went into file browser just to make sure since i am launching my command from desktop in terminal and there is no directory when i go to root then ect.

sorry, I am new to this, but I did get my new uuid, but am I supposed to replace the root uuid or replace the new partition with the root's uuid (just want to clarify)

Thanks for the help tho :)

---

### Post by bodhi.zazen on 2008-01-07
1. First I advise Ext3 over Ext2 (Ext3 is journaled and will be more reliable in preserving data).

2. use : ```
gksu gedit /etc/fstab
``` to edit fstab.

3. Use the uuid of your new partition (as seen in blkid).

See this link for info on fstab (and options)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by ckamc on 2008-01-07
Thank you :)

---

### Post by ckamc on 2008-01-10
So I put this off for a bit as I started to mess with gnome looks and today I went ahead and changed the uuid.

restarted and no longer got a message but I am still unable to create folders or save anything into the partition.

why wont it let me?

---

### Post by ckamc on 2008-01-10
i checked fstab again and fouind

> # /dev/hda7
UUID=881a961b-a7bf-4009-8972-60f110c4bcf1 /media/hda7     ext3    defaults        0       2


and the main linux portion reads
> 
# /dev/hda6
UUID=efb69d3d-ed07-4cf5-81a3-8c1c91dacd26 /               ext3    defaults,errors=remount-ro 0   

do I need to ad errors=remount-ro 0 to my hda7 to get permission?

---

### Post by ckamc on 2008-01-10
well i tried to set it to rw but now the partition does not display.....

what did I do wrong? I read the fstab thread and thought u did it correctly unless I am supposed to change it to ro? but thats read only....

---

### Post by bodhi.zazen on 2008-01-10
This entry in fstab looks fine to me :

> # /dev/hda7
UUID=881a961b-a7bf-4009-8972-60f110c4bcf1 /media/hda7 ext3 defaults 0 2

No, you do not need "errors=remount-ro" for hda7

Make sure the uuid is correct :

```
blkid
```

If it is correct, then :

```
sudo chmod 777 /media/hda7
```

How are you trying to access the space ? It is in /media/hda7.

---

### Post by ckamc on 2008-01-10
hmm not sure what the problem was before but now it works

thanks for your time.

---

