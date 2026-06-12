---
title: "Permissions confusing me [KUBUNTU]"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Anbern on 2006-11-15
I don't have the permission to change song tags in Amarok, i don't have the permissions to save imagefiles etcetera if i don't run them via gksudo, and I don't really think the way to go is gksudo <app> just because I want to be able to save an image.

Is there away around this so I can save normally from my regular account and don't have to use gksudo to be able to do the things I like?

---

### Post by taurus on 2006-11-15
Where do you plan to save all those things to?  You only have write permission to your own $HOME directory so if you want to save anything outside of that, you need to use either sudo or gksudo...

---

### Post by frodon on 2006-11-15
It sounds like a wrong fstab line.

Could you tell us the filesystem used by the partition where you want to save the file and then post here the content of your fstab file (type "sudo gedit /etc/fstab" in a terminal to open it).

Taurus's point is also valid.

---

### Post by Anbern on 2006-11-15
Okay, well I want to save it to /opt/lampp/htdocs/ but I guess I'll have to save it in my homedir and sudo mv it, as for Amarok I don't get it because the files is on my desktop, thus I should have the permission to change the tags on them. I've tried chmod 777 chowner etc.

Oh and my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c7514989-f744-4118-94cd-19c9c440a744 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=45071cad-f211-483b-b379-7afeae61f0de none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Ben Sprinkle on 2006-11-15
I can't stand chmod, for Amarok just gksudo it.

---

