---
title: "Move /home to new drive"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-05-25
I've got Feisty installed on my second hard drive, I still have Dapper on part of my Windows hard drive.

I'd like to move my old /home to the new Feisty /home partition, preserving settings.

I've looked at PartImage, and at [www.psychocats.net](www.psychocats.net), as well as this thread [http://ubuntuforums.org/showthread.php?t=445140](http://ubuntuforums.org/showthread.php?t=445140)

What would be the best way to do this? I'm a bit nervous about "translating" terminal commands when I'm not sure what they're doing. :)

TIA

---

### Post by Happy_Man on 2007-05-25
I would suggest [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome). It is totally safe, and I can vouch for it, having done it myself. Totally painless. :D

---

### Post by freesitebuilder on 2007-05-25
I forgot - I've got 3 other users that I want to move as well. Can I just repeat the commands for each username/home?

---

### Post by psusi on 2007-05-25
Just copy all of the files in the old /home to the new one.  

I suggest that you boot into rescue mode to do this.  If you have the old partition mounted in /media/hda2, then just do cp -a /media/hda2/home/* /home/

---

### Post by freesitebuilder on 2007-05-25
That didn't work - this is my fstab contents:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e27c3bdd-f406-4b36-bce0-43194b8f60d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=fc54f5d1-d567-4ef2-ab68-9bf356d1facd /home           ext3    defaults        0       2
# /dev/hda3
UUID=ACA6-45C0  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=CCE9-0485  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=7e37592d-06d7-4dfd-bc27-2d507385d7df /media/hda6     ext3    defaults        0       2
# /dev/hda8
UUID=d604cebf-6454-4408-8e62-36eb79fe84bb /media/hda8     ext3    defaults        0       2
# /dev/hda7
UUID=1906c7b3-5404-4007-b673-cb047aa688db none            swap    sw              0       0
# /dev/hdb2
UUID=9bc9d7f8-c39b-4915-9802-fa3665f71fe5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

My old /home is hda8, my new /home is hdb3

Should I remove other users, and start again? Then add the other users afterwards? But can I move their home directories too?

psusi - sorry, posted this while you were posting!

---

### Post by balak on 2007-05-25
I did a very similar thing just last week.

Boot into dapper, copy all the contents of your /home (older) to the /media/hdb3/

Use this command for copying

> cd /home/  && find . -depth -print0 | cpio --null --sparse -pvd /media/hdb3/

Then boot into feisty and you'll have all your directories.

Depending on the permissions, you may have to insert "sudo" in your commands (before the "cd" or before the "cpio").

---

### Post by dannyboy79 on 2007-05-25
or just use partimage.

---

### Post by bluknight on 2007-05-26
> **freesitebuilder said:**
> 
I'd like to move my old /home to the new Feisty /home partition, preserving settings.
TIA

Ive read the replies to your posts but it is not so easy as suggested depending on the version. For Dapper when I had to resize my /home partition all logins were locked out until the permissions and ownership of home folders were restored (as well as the .dmrc problem). Also if your /etc/fstab contains UUIDs your system may not boot completely. I suspect for Feisty it is even more perilous.

However if you want to set up a separate partition BEFORE the install then the helper urls applies.

If you want to know the details of doing it properly AFTER installation follow this thread (and the solution):

[http://ubuntuforums.org/showthread.php?t=454339](http://ubuntuforums.org/showthread.php?t=454339)

Good luck! (and of course post back for more)

---

### Post by freesitebuilder on 2007-05-26
I did something that locked out my /home on Dapper, so I've decided to copy over the folders manually, and re-install stuff (there wasn't a lot).

Next time should be straightforward, as I can do an upgrade, and my /home partition should still be plenty big enough.

Thanks for all the help!

---

