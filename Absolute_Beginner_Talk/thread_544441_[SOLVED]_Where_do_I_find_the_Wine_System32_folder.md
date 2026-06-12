---
title: "[SOLVED] Where do I find the Wine System32 folder??"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-06
I need to copy two files from my desktop into this folder but can't seem to find it.

Can anyone show me where to find it?

Thanks :)

---

### Post by Mothinator on 2007-09-06
It should be located at ~/.wine/drive_c/windows/system32

The wine directory itself is hidden, which is indicated by the leading '.'

---

### Post by aconley1 on 2007-09-06
Go to ~/.wine/drive_c/windows/system32

---

### Post by chrome307 on 2007-09-06
Thanks for telling me where it is but I'm still none the wiser :confused:

[IMG]http://i6.tinypic.com/52z993t.jpg[/IMG]

---

### Post by graigsmith on 2007-09-06
oh, your looking in the root "/" directory. 

the .wine folder is in your home folder.

the ~ in front of the filename they gave you means it's in your homefolder.  the file system understands that too. so if you have a script or something you can actually use ~/.wine    > it's a nice feature to have when your a system admin, cause you can write 1 script and use it for all users.

---

### Post by chrome307 on 2007-09-06
Thank You for letting me know ..... needed to view 'Hidden Files' but got there in the end :)

---

