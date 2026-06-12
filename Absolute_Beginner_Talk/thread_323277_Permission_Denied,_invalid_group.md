---
title: "Permission Denied, invalid group"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Whitey_McWhite on 2006-12-21
My graphics f'd up so I got a new video driver (.run file) burned it to a disc. So I go to the command prompt, mount the cdrom and such, but even when in sudo, whenever I try to execute the install file it says Permission denied. I tried chmod, chown, and some md5sum thing I found on here, and none worked. chown seemed like it almost got it, but it says invalid group. What does that mean? Would that fix it? If not how can I get it to allow me to execute the file? thanks in advance

---

### Post by taurus on 2006-12-21
You can't "chmod" files on CD since it's a read-only device!!!  You need to copy whatever files on the CD to the harddrive before you can change the permission...

---

### Post by scrooge_74 on 2006-12-21
only root user (using sudo) have permissions to install things

md5sum is to check that the file is ok, chown is for asigning owner to file, chmod is that one that will let make the file executable.

At your video driver website they don't have howto on installing the drivers?

did you try sudo sh the_name_of_the_file?

Why it never occurred to me that you had not copied into the HD? :D

---

