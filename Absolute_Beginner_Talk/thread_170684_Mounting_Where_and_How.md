---
title: "Mounting: Where and How"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by charlie. on 2006-05-05
While mounting is not new to me, there are two things that I always wondered about...

I know that if I want a mount to be re-mounted at every start, I must place it in **/etc/fstab**. I know that I can then make these changes take effect by running **sudo mount -a**. I have noticed, however, that this does not *unmount* any mounts that are *not* in /etc/fstab - thus giving a potentially false indication of what will be mounted after the next reboot. Is there a way to make the *mount* command clear all current mounts and then mount *only* what is in the fstab file?

I see that ubuntu has two folders: **/media** and **/mnt**. I also see a /cdrom folder that appears to be used for the CD rom when it is automatically mounted by APT. On previous systems, I have always mounted drives in **/mnt**. Are there any recommendations for mounting drives (with no special significance) in specific or commonly used locations?

Thanks for any information.

---

### Post by htinn on 2006-05-05
It's probably not a good idea to umount everything. If you're worried about it, you can simply reboot (but IMHO that's overkill).

In any case, use "mount" all by itself to see what is mounted and "sudo umount /path/to" to unmount whatever you don't want mounted.

Most of the forum and wiki guides will suggest placing partitions in the /media folder although /mnt (or really just about anywhere) will also work fine.

---

### Post by a_0000 on 2006-05-05
[QUOTE=htinn]It's probably not a good idea to umount everything. If you're worried about it, you can simply reboot (but IMHO that's overkill).

In any case, use "mount" all by itself to see what is mounted and "sudo umount /path/to" to unmount whatever you don't want mounted.

Most of the forum and wiki guides will suggest placing partitions in the /media folder although /mnt (or really just about anywhere) will also work fine.[/QUOTE]

is there a difference between /media or /mnt in terms of operation?

---

### Post by htinn on 2006-05-05
[QUOTE=a_0000]is there a difference between /media or /mnt in terms of operation?[/QUOTE]

Not in Ubuntu. It's conceivable that some future version will treat /media a little differently, but I sincerely hope they don't go that route. :-x

---

