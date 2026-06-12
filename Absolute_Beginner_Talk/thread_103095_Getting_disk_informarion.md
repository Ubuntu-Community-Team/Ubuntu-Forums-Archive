---
title: "Getting disk informarion"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-12-13
How do i do an ls that shows the disk used and disk free information. I have looked on lots of dos2linux command references but cannot find an alternative command.

The reason im needing this is there seems to be a big bug in the gnomes system>admin>disks thingy it never seems to report free space correctly.

Also, is it possible to modify the ls command ie - to list in -la format without continually having to add -la because i cant stand the accross the screen default view.
(like you could the dir command in dos to do say, list all files with sizes in alphabetical order).

---

### Post by e2k on 2005-12-13
To get the used and free space on your harddrives, you can type:
```
$ df -h
```
If you want to check how much a folder is taking (ex. your home), you can get it with:
```
$ du -h /home/user/
```

To answer your second question, you can edit some aliases in ~/.bashrc
If you want to add -la to the normal ls, you can edit the following line:
```
    alias ls='ls --color=auto'
```
Just put in **-la** after ls and it should do that automatically :)

---

### Post by dgrafix on 2005-12-13
great stuff :)

---

