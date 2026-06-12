---
title: "second disk"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Vandorius on 2007-03-25
Hey guys!

I have some problem seeing the contents of the scond disk. I can see the files going in trough root terminal. I dont thave permissions to view it trough konqueror. So how do ichange permission to /media/floppy0 or how do i copy files from this disk to my disk via terminal. 

Thanks a bunch!

---

### Post by eljalill on 2007-03-25
Via terminal you can us the "cp" command to copy. Use "man cp" to get the manual for the command with the syntax.
But it might make more sense to change permission: I would try using the "chown" command to change the owner to your user. That way you will get access.
again man "chown" gives examples how to use it.

Does that solve it?

---

