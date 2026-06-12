---
title: "permission denied"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by eatloaf on 2008-02-08
I'm trying to a remove a file where I am the owner and I have full rights (rwx)  but I get a 'Permission denied' error unless i use sudo.

Is there something I'm missing? I thought all I needed is to be the user and have rwx permissions.

---

### Post by Cresho on 2008-02-08
you may need to sudo nautilus and delete the file if that is your intention.  or copy text and paste it in a new one.  not sure.  Anyway, there are many ways doing this and its not a problem.

---

### Post by kpkeerthi on 2008-02-08
Can you post the output of ```
ls -l /path/to/the/file
```?

---

### Post by eatloaf on 2008-02-08
-rwxrwxrwx 1 ido ido 19442596 2007-11-07 01:13 /mnt/raid5/home/ido/backup/docsnsettings/My Documents/My Videos/maya_1.wmv

---

### Post by eatloaf on 2008-02-08
> **Cresho said:**
> you may need to sudo nautilus and delete the file if that is your intention.  or copy text and paste it in a new one.  not sure.  Anyway, there are many ways doing this and its not a problem.
The problem isn't this specific file. I have an automated process for backing up my desktop and it's failing on certain files. 

When I log on to the server and try to manually delete them, I get the permissions denied error, which is what I'm posting about, since it doesn't jive with what I understand about linux permissions.

---

