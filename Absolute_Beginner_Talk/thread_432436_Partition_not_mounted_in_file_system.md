---
title: "Partition not mounted in file system"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by jbor7755 on 2007-05-04
I have a partition (in FAT 32) for sharing files between Windows XP and Ubuntu Dapper.  However I didn't give it a name when I performed the partition/install so it sits on the desktop as "sda4". I can acces by double click but I have no idea how to access it by the command prompt. I really want to remount it as "/share" so it is easier to send files there from the prompt and it becomes "my" folder.

I also do not know which network-manager I should use for wireless network access at my university. There appears to be a few options in synaptic.

Any ideas?

---

### Post by antoz on 2007-05-04
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

These links are helfull for mounting partitions

---

### Post by ubnewbie2 on 2007-05-04
Is it mounted already?  My install put all the spare partitions in /media, e.g. /media/disk1, /media/disk2 etc

Anyway it looks like it is device sda4, so you should be able to remount it wherever you want.  I'd suggest under the /mnt directory.  Create a directory called /mnt/share and...

sudo mount /dev/sda4 /mnt/share

You might need to set ownership and/or permissions to use it.

To make it permanent, you'll need to edit fstab.

---

### Post by jbor7755 on 2007-05-04
Ha haaaaa!

It's in media!

I can get to it now and read from it. I guess that means it should be fine and I can write to it from the command prompt.

Thanks for your help.

I guess I can remaount at a later stage if neccessary

---

