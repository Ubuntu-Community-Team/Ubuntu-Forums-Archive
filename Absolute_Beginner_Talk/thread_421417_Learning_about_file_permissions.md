---
title: "Learning about file permissions"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by nvteighen on 2007-04-24
Well, I continue teaching myself in the ways of Linux using the Feisty live CD. Today, "lesson" (taught by myself!) was on chmod/chown and think I've learned a lot. And discovered that I feel much more comfortable using the octal permission format rather than with the letters...

My questions are a bit technical. 

1) If you allow a **directory** to be readable, but not executable (say 644 and assuming the user is the owner), you can't go in... then isn't it unreadable? Which is the **exact** difference between read and execute in directory permissions?

2) Theoretically, if a file is write-only (-w- or 2), you could write on it, but how do you do that if you can't even open it? I assume there must be a way... or write-only permission is meant to some kind of background-processes (like Windows' "services").

Wow, how many Windows problems could I have avoided if I had discovered Linux before!

---

### Post by Eclipse. on 2007-04-24
Using "sudo" before any command will give you full permissions with whatever you are doing.

---

### Post by anaconda on 2007-04-24
> **nvteighen said:**
> Well, I continue teaching myself in the ways of Linux using the Feisty live CD. Today, "lesson" (taught by myself!) was on chmod/chown and think I've learned a lot. And discovered that I feel much more comfortable using the octal permission format rather than with the letters...

My questions are a bit technical. 

1) If you allow a **directory** to be readable, but not executable (say 644 and assuming the user is the owner), you can't go in... then isn't it unreadable? Which is the **exact** difference between read and execute in directory permissions?

actually changing to a directory means the same than executing a directory file ( . or ..)  so directories are a special case.

> 2) Theoretically, if a file is write-only (-w- or 2), you could write on it, but how do you do that if you can't even open it? I assume there must be a way... or write-only permission is meant to some kind of background-processes (like Windows' "services").

If you have only writing permissions to a file then you can overwrite it destroying its previous contents. But realistically usually when you have w rights you also have r. 

> Wow, how many Windows problems could I have avoided if I had discovered Linux before!

:)  propably most of them..  ;)

---

### Post by nvteighen on 2007-04-24
Aha! Thanks. If you only have -w-, you can create a new file with same file and overwrite... I know it's more a theorical scenario to give write-only permission, but I want to learn! Thank you very much.

But I still don't understand the directory problem. What I mean is this: what means that you can "read" a directory. In a simplier way: if a direactory has rw- permission, how do you "read" not being able to "execute"? Is there a command?

---

### Post by Najand on 2007-04-24
1. The basic r, w, and x permissions have slightly different meanings for directories than they do for files. If a directory is readable it means that a user can look into it and see what files are there. Write permission allows a user to add, delete or rename files in the directory. Directories cannot be executed in the same way that files can. Execute permission for directory is also referred to as search permission, as it controls the ability to cd through the directory structure. 

2. You cannot edit files even if you have only write permission and no read permission. You can just delete/rename them or just overwrite some other files on them.

---

### Post by nvteighen on 2007-04-24
> **Najand said:**
> 1. The basic r, w, and x permissions have slightly different meanings for directories than they do for files. If a directory is readable it means that a user can look into it and see what files are there. Write permission allows a user to add, delete or rename files in the directory. Directories cannot be executed in the same way that files can. Execute permission for directory is also referred to as search permission, as it controls the ability to cd through the directory structure. 

2. You cannot edit files even if you have only write permission and no read permission. You can just delete/rename them or just overwrite some other files on them.
Ok, but the problem I have is that, if I don't allow execution to directory AAA, then, I can't do "cd AAA". Thus, I can't see what files there are inside!... Or is something like "ls /AAA" allowed to list a directory's content without executing?

(Pardon, but I'm a beginner...)

---

### Post by Najand on 2007-04-24
Without "x" and with "r", you cannot execute "cd/AAA" command. However "ls /AAA" shows the filenames in it. It is interesting that it is just names; if you try "ls -a /AAA" you will recieve something like:
```

?--------- ? ? ? ?                ? AAA/a

```

---

### Post by nvteighen on 2007-04-24
> **Najand said:**
> Without "x" and with "r", you cannot execute "cd/AAA" command. However "ls /AAA" shows the filenames in it. It is interesting that it is just names; if you try "ls -a /AAA" you will recieve something like:
```

?--------- ? ? ? ?                ? AAA/a

```
Thank you! It is **exactly** what I needed to understand! :D

---

