---
title: "Recover settings"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Bothered on 2007-09-14
I recently destroyed my home directory. I've since recovered what I can from a backup, but I didn't bother recovering the hidden files (and I've since replaced my backup). As such I've lost files which you would normally expect to have in your home folder, such as .bashrc. Is there any way for me to find out which files I'm missing, and to restore them to the defaults? Would it, for example, be ok to create a dummy user and copy over the missing files from the home folder that would be generated for them?

---

### Post by kuja on 2007-09-14
> **Bothered said:**
> I recently destroyed my home directory. I've since recovered what I can from a backup, but I didn't bother recovering the hidden files (and I've since replaced my backup). As such I've lost files which you would normally expect to have in your home folder, such as .bashrc. Is there any way for me to find out which files I'm missing, and to restore them to the defaults? Would it, for example, be ok to create a dummy user and copy over the missing files from the home folder that would be generated for them?

The dummy account method should work well.

---

### Post by ajgreeny on 2007-09-14
But I'm a bit baffled as to why a dummy account is any better or easier than just making your own supply of hidden files.  Most of them are made when you open the particular program or application the first time, and the config files will be changed to what you want when you change the configuration of each application, ie to make it look as you wish.  Why are dummy user files and folders copied across better?  Perhaps I've just missed the point of your question.
EDIT  OK, I've reread your post and see what your problem is with those files that are not config or hidden application folders.  Are the files not just restored when you next boot the computer?  I ask this as I admit I don't know, but I assume from your question they are not.

---

### Post by Bothered on 2007-09-15
I assumed that they would all be recreated, hence I didn't restore them from the backup. Apparently they're not, as I'm missing a .bashrc file.

---

### Post by Bothered on 2007-09-15
EDIT: Duplicate post.

---

### Post by louieb on 2007-09-15
[FONT=Arial]When you add a new user it looks in /etc/skel/ and copies the files from there to the new users home directory. You can find the default .bashrc there. After the copy just make sure the copy in your home directory is owned by you.   [/FONT]

---

### Post by Bothered on 2007-09-15
> **louieb said:**
> [FONT=Arial]When you add a new user it looks in /etc/skel/ and copies the files from there to the new users home directory. You can find the default .bashrc there. After the copy just make sure the copy in your home directory is owned by you.   [/FONT]

Thanks, that was I was looking for. Files restored.

---

