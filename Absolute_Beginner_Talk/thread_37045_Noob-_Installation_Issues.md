---
title: "Noob- Installation Issues"
date: 2005-05-25
forum: Absolute Beginner Talk
---

### Post by darkbane on 2005-05-25
I don't know if I'm just completely missing something obvious, or if something is going wrong with my installation.

Here's My issue

I have two Partitions on my hard drive.  I have a primary partition for windows and I created a second partition to install linux on.  

In the installation I go to my partition settings for my Linux Partition.  I don't know what Filesystem I should use, so I kept it at Fat32, the bootable flag is on.  My mount options are set at default, but now I don't know what to put for my Mount Point.  When I try to "Finish partitioning and write change to disk" it does nothing but refresh the screen back to the same menu.  

Is this making any since?

I'd appreciate any help.  This is my first time trying to install linux.  I'm want to dual boot to windows xp.

Thanx

---

### Post by the_clown on 2005-05-25
[QUOTE=darkbane]I don't know if I'm just completely missing something obvious, or if something is going wrong with my installation.

Here's My issue

I have two Partitions on my hard drive.  I have a primary partition for windows and I created a second partition to install linux on.  

In the installation I go to my partition settings for my Linux Partition.  I don't know what Filesystem I should use, so I kept it at Fat32, the bootable flag is on.  My mount options are set at default, but now I don't know what to put for my Mount Point.  When I try to "Finish partitioning and write change to disk" it does nothing but refresh the screen back to the same menu.  

Is this making any since?

I'd appreciate any help.  This is my first time trying to install linux.  I'm want to dual boot to windows xp.

Thanx[/QUOTE]
 Are you trying to install ubuntu on the fat32 partition?

---

### Post by darkbane on 2005-05-25
I'm not sure which file system to use, so I had it on Fat32.   Which file system should I use?

---

### Post by the_clown on 2005-05-25
Use the ubuntu installer to delete the empty fat32 partition, then tell ubuntu to install in the free space.

---

### Post by Gandalf on 2005-05-25
[QUOTE=the_clown]Use the ubuntu installer to delete the empty fat32 partition, then tell ubuntu to install in the free space.[/QUOTE]
 you should use like this, i suppose you have a free partiton with 40 GB and u have 512Mb ram

so first delete the fat partiton (look into the partitioner there's an option to delete it)
then create a partiton with 39Gb space, ext3 filesystem (not FAT32!), mount point /
create another partiton with 1gb (the rest), swap filesystem, no mount point

and continue, hope it helps

---

### Post by darkbane on 2005-05-25
I just picked a different file system to use and it's installing now.  I really have no idea what the differences between the file systems are.  I've been trying to read up on the linux terms, but there's a lot of stuff to read.  I can't absorb it all.  

I'm more of a "trial and error" type of guy, so we shall see what happens with my installation.

I'll keep posted on my installation.  I'm sure I'm going to have some other issues in the near future

---

### Post by Gandalf on 2005-05-25
what filesystem did u used? did u create a swap?

---

### Post by darkbane on 2005-05-25
Can I change the file system once I have installed it, or would I have to reinstall Ubuntu all together in order to completely change the file system?

---

### Post by darkbane on 2005-05-25
I think I used Ext2,  and no I didn't create a swap

---

### Post by Gandalf on 2005-05-25
[QUOTE=darkbane]Can I change the file system once I have installed it, or would I have to reinstall Ubuntu all together in order to completely change the file system?[/QUOTE]
 you can change/resize, you need live CD in order to do it

---

### Post by darkbane on 2005-05-25
well I might be asking you how to do that eventually

---

### Post by Gandalf on 2005-05-25
[QUOTE=darkbane]well I might be asking you how to do that eventually[/QUOTE]
 u need live CD and gparted
```

sudo apt-get install gparted

```

---

### Post by darkbane on 2005-05-25
I have the live CD, where do I get "gparted"

---

### Post by Gandalf on 2005-05-25
[QUOTE=darkbane]I have the live CD, where do I get "gparted"[/QUOTE]
 by the command line as i descriped above
take a look to [http://ubuntuguide.org/#gparted](http://ubuntuguide.org/#gparted) and try also to browse it, it fits noobs

---

### Post by darkbane on 2005-05-25
[QUOTE=Gandalf]by the command line as i descriped above
take a look to [http://ubuntuguide.org/#gparted](http://ubuntuguide.org/#gparted) and try also to browse it, it fits noobs[/QUOTE]
 I'm trying to install Gparted.  Bare with me.  I'm not a computer Novice, but I am completely new to Linux.  I ran the command line stated above, bu I get an error saying

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"

I have absolutely no idea what this means.

---

### Post by darkbane on 2005-05-25
Can anybody give me some incite as to what I need to do?

---

### Post by poofyhairguy on 2005-05-26
[QUOTE=darkbane]
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"

I have absolutely no idea what this means.[/QUOTE]

That means you need to run this command in the terminal:

sudo dpkg --configure -a

I've seen it a lot.

---

