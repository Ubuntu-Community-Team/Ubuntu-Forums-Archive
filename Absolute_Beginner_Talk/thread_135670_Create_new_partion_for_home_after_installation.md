---
title: "Create new partion for /home after installation"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by daredevil on 2006-02-24
I wish to create a separate partion for /home directory but am not interested in reinstalling kubuntu again. Is that possible for me to create a new partition using GParted and assign the mount point of /home to the newly created partion...

---

### Post by austin on 2006-02-24
I have created a link from my home to a separate data partition. it's just one click more to go there, and you don't have to mess up your system ...

---

### Post by bored2k on 2006-02-24
[QUOTE=daredevil]I wish to create a separate partion for /home directory but am not interested in reinstalling kubuntu again. Is that possible for me to create a new partition using GParted and assign the mount point of /home to the newly created partion...[/QUOTE]
Yes. You just need to add an entry to your /etc/fstab file. An example of an separate  ext3 /home would be:
```
/dev/hda3       /home           ext3    defaults        0       2
```

After that, you  could move your home directory there, simply reboot **or** do a ```
sudo mount -a
```. I'd recommend rebooting because you don't want to reassign mount points while using /home.

---

### Post by bored2k on 2006-02-24
[QUOTE=austin]I have created a link from my home to a separate data partition. it's just one click more to go there, and you don't have to mess up your system ...[/QUOTE]
It doesn't mess up your system. At all.

---

### Post by mjfleck2000 on 2006-02-24
[QUOTE=daredevil]I wish to create a separate partion for /home directory but am not interested in reinstalling kubuntu again. Is that possible for me to create a new partition using GParted and assign the mount point of /home to the newly created partion...[/QUOTE]

Note that GParted will not resize a mounted partition.  So, if you present setup is something like:
/dev/hda1       /
/dev/hda2     Extended partition
/dev/hda5     Swap

you would be booting into the /dev/hda1 partition (your root directory) and GParted would not resize it.
You could use the Dapper LiveCD, run GParted from within  LiveCD, then reboot into your new setup. (You need to edit /etc/fstab and "cp -a" for your present home to the new home partition).

Mike

---

### Post by cotcot on 2006-02-24
Maybe this could help : [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by daredevil on 2006-02-24
Thank u all for ur valuable suggestions. That blog was good

---

### Post by dvarsam on 2006-02-25
Yes, but what happens when you need to Format Ubuntu?

How can you tell Mozilla Firefox, to also save it's "Bookmarks" (or in windows "favorites" ) inside the "/home" (which lies in a separate Partition)?

OR:

You can NOT do this & every time you want to Format, you have first to Backup "Bookmarks"?

---

### Post by aysiu on 2006-02-25
[QUOTE=dvarsam]Yes, but what happens when you need to Format Ubuntu?

How can you tell Mozilla Firefox, to also save it's "Bookmarks" (or in windows "favorites" ) inside the "/home" (which lies in a separate Partition)?

OR:

You can NOT do this & every time you want to Format, you have first to Backup "Bookmarks"?[/QUOTE] Firefox already saves its bookmarks inside the /home directory. Yours would be in /home/dvarsam/.mozilla

.mozilla is a hidden directory.

---

### Post by 1002285 on 2006-07-13
> **bored2k said:**
> Yes. You just need to add an entry to your /etc/fstab file. An example of an separate  ext3 /home would be:
```
/dev/hda3       /home           ext3    defaults        0       2
```

After that, you  could move your home directory there, simply reboot **or** do a ```
sudo mount -a
```. I'd recommend rebooting because you don't want to reassign mount points while using /home.

Thanks, I had the same issue.
But I have never understood, what do the numbers in the fstab lines actually mean.
For example you suggest
/dev/hda3       /home           ext3    defaults        0       2
but on another blog I found this:
/dev/hda5 /home ext3 nodev,nosuid 0 2
And why does your line have 0 and 2, while my line for the OS partition has 0 and 1 in the end?
(/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1)
Thanks anyway, I'm sure your suggestion works.

---

