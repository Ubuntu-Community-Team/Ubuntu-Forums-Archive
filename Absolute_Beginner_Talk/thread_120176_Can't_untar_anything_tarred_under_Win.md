---
title: "Can't untar anything tarred under Win"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Books on 2006-01-21
Hi. Under Windows I used 7-Zip to tar many files. Now, under Kubuntu, I can't untar any of them. It says...

Cannot utime: Operation not permitted

I can untar them using 7-Zip under Windows, so what gives? I tried the Extract command in Konqueror and tried Ark, both failed.

Any ideas?

---

### Post by Books on 2006-01-21
I forgot to mention something that might help. The Ark program can see the files in there, it just can't open them for some reason.

Thank you for helping!

---

### Post by cwaldbieser on 2006-01-21
[QUOTE=Books]I forgot to mention something that might help. The Ark program can see the files in there, it just can't open them for some reason.

Thank you for helping![/QUOTE]
utime has something to do with setting file permissions.  I would guess that maybe you are trying to uncompress it somewhere you don't have permission?

---

### Post by Books on 2006-01-21
[QUOTE=cwaldbieser]utime has something to do with setting file permissions.  I would guess that maybe you are trying to uncompress it somewhere you don't have permission?[/QUOTE]

Wow, I hadn't considered that. I'm new to Linux -- less than a month. How would I check user permissions?

---

### Post by cwaldbieser on 2006-01-21
[QUOTE=Books]Wow, I hadn't considered that. I'm new to Linux -- less than a month. How would I check user permissions?[/QUOTE]
Well, the file browser you are using (e.g. nautilus, konqueror) probably has a view mode that shows info including persmissions on files and folders.  If you go to a terminal and type:
```

$ ls -l

```
That also shows you the "l"ong list.  Permissions look like:
rwxrwxrwx
for example.  There are 3 groups of "rwx" slots.  These groupings correspond to permissions for the user, for the group members, and for everyone else.  If a permission is absent, it shows up as "-".  So,
rwxr--r--
means the user can read write and execute the file.  Group members can read it, and everyone else can read it.  There are a few more subtleties, but those are the basics.

---

### Post by ubuntuuser on 2006-01-21
Maybe the files are still on your Windows partition when you try to unpack them? If so, and you have NTFS as filesystem on your Win partition, linux can't write on it and will probably give you some kind of error. Copying the tar-files to /home/$USER could help in that case.

---

### Post by GreyFox503 on 2006-01-21
Yes, try extracting them to your home directory or desktop where you have permission to write.

---

