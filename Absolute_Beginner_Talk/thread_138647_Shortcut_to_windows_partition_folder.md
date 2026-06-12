---
title: "Shortcut to windows partition folder"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by daredevil on 2006-03-02
Normal link for a file within same partition can be created using

```

ln <source file> <dest folder with linkname>

eg: ln ~/linux.txt ~/Desktop/linux
```

My question:

I have mounted fat32 partition under the directory /windows. Within that i have a folder named say "abc"(plz note its a folder). My aim is to create a keyboard shortcut for that folder. Since there is no option available to do so, i decided to create a link to this folder on my ~/Desktop directory and then add the link to KMenu and finally assign it a keyboard shortcut. I tried this command and it threw me an error

```
sriram@Home:~$ ln /windows/abc ~/Desktop/abc
ln: `/windows/abc': hard link not allowed for directory
sriram@Home:~$
```

Can anybody help me to create a Hard link for that folder
Thnx in advance

---

### Post by carlosqueso on 2006-03-02
can you create a symlink with ```
ln -s /windows/abc ~/Desktop/abc
```  That's what I did and it worked fine.

---

### Post by daredevil on 2006-03-02
Oh great carlosquesco. It worked perfectly.

Thnx a million

---

### Post by carlosqueso on 2006-03-02
No problem.

---

### Post by thenewbeat on 2007-11-07
When I create symlinks to my Vista partition they have a padlock on them. So, I can only read the files. 

Normally when I open Nautilus and navigate to the Vista drive I can write to it fine. How can I make these symlinks link to folders that are writable?

---

### Post by thenewbeat on 2007-11-07
Answered my own question... I didn't have "Enable write support for internal drives" selected in the NTFS Configuration Tool.

---

