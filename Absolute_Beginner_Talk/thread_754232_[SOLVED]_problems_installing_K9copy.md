---
title: "[SOLVED] problems installing K9copy"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by jfluet on 2008-04-13
i tried sudo apt-get install k9copy in the terminal and this is what i got
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package k9copy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package k9copy has no installation candidate

the same thing happens with the Prerequisit,
    *  DVDAuthor
    * libdvdread
    * growisofs
    * mencoder
    * mplayer
    * libhal
    * libdbus
    * libdbus-qt
any help i would appreciate!
thanks a bunch!

---

### Post by forestpixie on 2008-04-13
Can you install anything - have you done something to the sources?

Post it here if you're not sure

```
cat /etc/apt/sources.list
```

---

### Post by jfluet on 2008-04-13
cat: /etc/apt/sources.list: No such file or directory
if i did something i don't know what i did! 
this is the first time i had a problem that i cant figure it out??
and nothing will install

---

### Post by forestpixie on 2008-04-13
can you do this in a terminal

```
ls /etc/apt/sources*
```

---

### Post by ghost_ryder35 on 2008-04-13
go to system,administration,software sources, third party, and enable all the sources.  then 
```

sudo apt-get update

```
and run the k9 install command again

---

### Post by forestpixie on 2008-04-13
If you've lost the whole lot you might need to enable the repos on the first tab as well.

---

### Post by jfluet on 2008-04-13
this is what i got 
/etc/apt/sources.list_backup  /etc/apt/sources.list.save

/etc/apt/sources.list.d:

but the sudo apt-get update stuff worked thanks!

---

### Post by ghost_ryder35 on 2008-04-13
> **jfluet said:**
> this is what i got 
/etc/apt/sources.list_backup /etc/apt/sources.list.save
 
/etc/apt/sources.list.d:
 
but the sudo apt-get update stuff worked thanks!
I know ;)

---

