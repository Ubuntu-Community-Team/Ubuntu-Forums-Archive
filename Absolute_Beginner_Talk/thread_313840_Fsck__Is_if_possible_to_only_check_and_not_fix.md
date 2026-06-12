---
title: "Fsck:  Is if possible to only check and not fix?"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Gen2ly on 2006-12-06
Really sounds easy but I did an exhaustive look and couldn't find it.  Is there a way to have fsck just check the mounted partition I'm using?  I did:
> fsck -sn /dev/hd#

I know howto have it check on next boot...
> sudo shutdown -Fr now
sudo touch /forcefsck

but I was hoping to learn how to just check the file system.

---

### Post by john.nicholls on 2006-12-07
According to "man fsck" fsck -N "don't execute, just show what should be done".

John

---

### Post by ciscosurfer on 2006-12-07
I agree that you should check out the **man fsck** page for info on how to accomplish this task.

---

### Post by Gen2ly on 2006-12-07
Appreciate the help!  For some weird reason it wasn't working last night.  Just a few clicks and then stop.  Works now though.  Oh, BTW,
> fsck -sn /dev/hd#
is the correct line.

---

