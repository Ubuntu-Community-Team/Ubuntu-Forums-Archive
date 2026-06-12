---
title: "Need help adding disk space"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by gcos7 on 2007-06-09
:DSince I've gotten this far with Ubuntu, I decided to shrink the size of my Windows partition, thus giving me more space for Linux (in particular, I want to try vmware player and run Windows XP as a vm within Ubuntu).  I am running 7.04.

I booted up using the LiveCD and then ran gparted so I could resize the Windows partition, then moved the swap file down next to the Windows partition, leaving me a 20gb free chunk in front of the Ubuntu ext3 partition.  I had gparted format the new partition as ext3.  Now I'm a little lost - I know I have to put something in fstab (?),  but I don't know what.  Is there a way to "add" this new partition to the existing file system so that Ubuntu will just use it when the need arises (such as running out of space on the original ext3 partition), or do I have more to do than I hope?;)

Thanks for your patience - I'm trying to get this all running so I can still have access to Family Tree Maker 10.0 but using Ubuntu as my main OS.

---

### Post by Bohlio on 2007-06-09
I dont think you can add it to the ubuntu partition unless it is after it, in this case it isn't. but to mount it, all you need to do is find out what the name is, then... ```
sudo mkdir /media/(name you want)
mount /dev/???? /media/(name you want)
```
Then you need to edit your fstab by typing in... ```
gksudo gedit /ect/fstab
```
And then add the line ```
/dev/???? /media/(name you want) ext3 defaults 0 0
```

Replace ???? with whatever your name is, and replace (name you want) with the name that you want :-P

---

### Post by ryanVickers on 2007-06-09
Could you just post a screenshot to show how it's setup?

> Is there a way to "add" this new partition to the existing file system so that Ubuntu will just use it when the need arises?
Yes, well, um:
If a new partition is created, it will automatically detect it and mount it at every boor, like normal, but it will most likelly show up as /media/disk or something like that, insted of /whatever (a branch of the root filesystem)

I would recommend a little package called Storage Divice Manager, that let's you easilly configure where you want to mount stuff - just be careful!  There's warnings to stop you from accedentally doing this, but just make sure you don't change the mount point of your root filesystem!

Edit: Why don't you justr expand the existing ubuntu partition into the empty space, or if this sounds dumb, then again, please post a screenshot of current setup so I can guide you through it! :)

---

### Post by gcos7 on 2007-06-09
;)Thanks!

---

### Post by starcraft.man on 2007-06-09
> **gcos7 said:**
> :DSince I've gotten this far with Ubuntu, I decided to shrink the size of my Windows partition, thus giving me more space for Linux (in particular, I want to try vmware player and run Windows XP as a vm within Ubuntu).  I am running 7.04.

I booted up using the LiveCD and then ran gparted so I could resize the Windows partition, then moved the swap file down next to the Windows partition, leaving me a 20gb free chunk in front of the Ubuntu ext3 partition.  I had gparted format the new partition as ext3.  Now I'm a little lost - I know I have to put something in fstab (?),  but I don't know what.  Is there a way to "add" this new partition to the existing file system so that Ubuntu will just use it when the need arises (such as running out of space on the original ext3 partition), or do I have more to do than I hope?;)

Thanks for your patience - I'm trying to get this all running so I can still have access to Family Tree Maker 10.0 but using Ubuntu as my main OS.

In addition to bohlio's answer, this is a [good tut]("http://www.psychocats.net/ubuntu/mountlinux") to doing it.

As for the VM, I don't recommend VMware player, its limited and won't give you as much options. Try [Virtual Box]("http://www.virtualbox.org/") first, you may be pleasantly surprised how powerful and well the free program is :D. Oh and they both have a debian in the download for feisty and a repo to add to your list, choose your method of install. >.>

---

