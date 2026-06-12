---
title: "How to access NTFS drives directly??"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by karanislove on 2006-09-25
Hi all, I m very new to Ubuntu so please treat me like a beginner... I also apologize if I've posted in the wrong thread..

I am not able to enter into any of my drives exept the main one. Computer has assigned them as hd1, hd2....hd5. Everytime I try to enter, it says "You do not have the permissions necessary to view the contents of "hdb5".". I was logged in as an admin. Then after fiddeling around a bit, I entered into System->Administration->Disks. From there I opened my drive and then copy and paste the link (/boot/hd1/songs) into my player then it worked. But still I cant look into them directly. 
Except the main drive all other are NTFS drives. Yesterday I find out that I also dont have write access to those drives.
Here is the details of fstab if it helps out in any way:-k 
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda2 /media/hda2 ntfs defaults 0 0
/dev/hda3 /media/hda3 ntfs defaults 0 0
/dev/hdb1 /media/hdb1 ntfs defaults 0 0
/dev/hdb5 /media/hdb5 ntfs defaults 0 0
/dev/hda4 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0


---

### Post by CatKiller on 2006-09-26
You're unlikely to get write access to those partitions - although Linux can happily read NTFS data, MS have kept all the details secret and so writing to an NTFS partition is sketchy, and may well go hideously wrong. My advice would be to read up on partitioning and resize one of those partitions to allow the creation of a FAT32 partition that Windows and Linux can both happily read and write to.

However, [this site]("http://ubuntuguide.org/wiki/Dapper") has details on how to mount an NTFS partition with write access, as well as details on how to do it read-only for all users.

---

### Post by xyz on 2006-09-26
Also  [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)  seems to work quite well for lots of people.
I'd sure like to get things cleared out as some people write:
> You're unlikely to get write access to those partitions
and others say you can. And it surely does work, doesn't it?

---

### Post by Bachstelze on 2006-09-26
Maybe not everyone knows about it ;)

---

### Post by xyz on 2006-09-26
> **HymnToLife said:**
> Maybe not everyone knows about it ;)
Probablement! No doubt you're right. Works for me!

---

### Post by CatKiller on 2006-09-26
> **xyz said:**
> Also  [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)  seems to work quite well for lots of people.
I'd sure like to get things cleared out as some people write:

and others say you can. And it surely does work, doesn't it?

Perhaps I should have said "you're unlikely to **want** write access on those partitions" :-D Every single thing that I've read says that it's experimental, and you shouldn't try it on data that you want to keep. If you don't want to keep the data, why would you want to change it? I've never tried, and I've got rid of all my NTFS partitions now. But you're right, people have reported some success in writing to an NTFS partition.

---

### Post by xyz on 2006-09-26
Writing to an NTFS partition does seem to have evolved in the right direction for dual-booters out of necessity or wish.
When I read the link I posted -and the thread's author sure knows A LOT more about it than I ever will- I tend to believe it esp. since he posts "proofs"...that worked for him/her.

But its' true...we'll never know for sure until we tried! ;) I was trying to get a clearer picture of why it works or not. I have no idea about this but...is it a question of HD/computer types? It doesn't make sense to me the reason why it works for some and not for others.

Also with the increasingly large (and...cheaper!) HD, FAT 32 solves it!
Thanks for replying.

---

