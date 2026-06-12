---
title: "Links to folders."
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2005-11-26
Can I create links for folders in the same way we can create links for files?

I mean:

I have a mount point called /mnt/drive_c

I would like to have a folder in my home directory that refers to that mount point.  I would like to use the /mnt/drive_c as if it were in my home directory.

---

### Post by Kvark on 2005-11-26
In this case you could edit /etc/fstab to use for example "/home/paulo/c" as mountpoint instead of "/mnt/drive_c".

---

### Post by paulozzzz on 2005-11-26
[QUOTE=Kvark]In this case you could edit /etc/fstab to use for example "/home/paulo/c" as mountpoint instead of "/mnt/drive_c".[/QUOTE]

Thanks.  It solves my particular problem.

But suppose I setup a file server and I need to share a similar mount point with my students, each one having access only to their home directories?

---

### Post by lcg on 2005-11-26
[QUOTE=paulozzzz]But suppose I setup a file server and I need to share a similar mount point with my students, each one having access only to their home directories?[/QUOTE]
You can put a symbolic link to the shared directory into each user's home.
```
man ln
``` will give you the details you need to know.

HTH,
Lars

---

### Post by Kvark on 2005-11-26
[QUOTE=paulozzzz]Thanks.  It solves my particular problem.

But suppose I setup a file server and I need to share a similar mount point with my students, each one having access only to their home directories?[/QUOTE]
You'll have to use symbolic links instead of hard links to point to directories, give ln the -s option to make a symbolic link.

---

### Post by paulozzzz on 2005-11-26
[QUOTE=lcg]You can put a symbolic link to the shared directory into each user's home.
```
man ln
``` will give you the details you need to know.

HTH,
Lars[/QUOTE]

Excelent.  Thanks.

---

### Post by paulozzzz on 2005-11-26
[QUOTE=Kvark]You'll have to use symbolic links instead of hard links to point to directories, give ln the -s option to make a symbolic link.[/QUOTE]

Yes, I read about the danger of a hard link in the Cookbook.:)

---

