---
title: "Hard Link across partition"
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

### Post by evilgold on 2006-03-02
As the error states: hard link is not allowed for a directory. Use soft link instead

```
ln -s /windows/abc ~/Desktop/abc
```

---

