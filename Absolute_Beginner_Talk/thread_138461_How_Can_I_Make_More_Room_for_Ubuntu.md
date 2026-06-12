---
title: "How Can I Make More Room for Ubuntu?"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by mrgnash on 2006-03-01
I'm rapidly running out of room on Ubuntu, and since I'm not using XP for anything other than playing a couple of games, I wondered what would be the best/easiest way to shrink that and then somehow allocate the space created for Ubuntu's use?

You can see my partition table below:

[IMG]http://img131.imageshack.us/img131/1129/snapshot15jc.png[/IMG]

... I'd probably want to give Ubuntu about 20gig of the space currently free on XP.

---

### Post by gord on 2006-03-02
aparently parted can shrink Fat32 drives just fine, allthough i don't use qparted myself, there should be an option to shrink it down.

there will then be extra space on your disk, you'll most likly have to create a new partition in there and then just add it to your fstab file.

as allways, make backups of important files first :)

---

### Post by mrgnash on 2006-03-02
When I try to resize the FAT32 partition qtparted just comes up with an error (unfortunately it just says '!' so I don't know what it means) and refuses to do anything :( What else should I use? 

The other thing is, what should I mount the new partition as, and what do I need to do with my fstab file? :confused:

---

### Post by soonindallas on 2006-03-02
if you booted from this disk the OS might disallow qparted from touching the partition table.  I did a lot of partition work without a hitch with gparted booted from a live cd: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

keep a ubuntu live cd handy in case you need to edit your /etc/fstab due to partition label changes as gparted will not update this file.

---

### Post by cotcot on 2006-03-02
Have you defragged the fat partitions ?

---

