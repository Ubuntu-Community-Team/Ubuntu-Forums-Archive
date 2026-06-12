---
title: "can't remove directories"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2007-08-27
I've got some directories I just can't get rid of.  I think it's in part because I moved and/or deleted files on them from a windows machine that had them mounted as network shares.  That probably shouldn't be a problem, but I don't know what else it could be from.

I've tried removing the files from windows and from ubuntu, as sudo and as the user, renaming them, removing the "." from the beginning of the file as in ".Trash-<username>" and I just can't figure it out.  I always get the error 

rm: cannot remove directory `1/other': File exists

(the directory is named 1)

nothing is showing up in the trash bin for me to empty, either.

Any suggestions? 

Thanks in advance

oh, this is on feisty, ntfs drive mounted as /media/uhold

---

### Post by Inxsible on 2007-08-27
What is the exact command that you are using?

Remember rm will not remove the directory unless its empty, so you might wanna look into the -R option (recursive). Of course, if its not in your home folder, then you will have to use sudo on it.

Something like ```
sudo rm -R /exactPathTo/1/
```

---

### Post by randomjohn on 2007-08-27
yeah, that's what I'm doing... sudo rm -Rf /path/directory/*

---

