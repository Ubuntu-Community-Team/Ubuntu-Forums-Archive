---
title: "Backing up for a fresh install - possible on my configuration?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by MikeMLP on 2006-09-06
To make a long story short: I messed up my install by trying to obtain edgy (I know that I wasn't supposed to do this, but before I tried upgrading, I had messed up my install significantly on my own, which would have resulted in a lot of fixing anyway - this is why I figured- why not give edgy a go)  And went it did.  Neither my old kernel nor the new one(s) that edgy installed will boot.  I'm really not surprised, or at all upset - it is probably a good idea to perform a fresh install anyway.  My question is as follows:

I did not partition /home separately - I started as a new user with  only 10 GB of space for the install and I wanted to make sure I didn't run out.  Therefore, if I want to save some of my documents, and settings, etc, would it be wise to back up my home folder to my fat partition, and then reinsert it once the fresh install is complete?  is this not virtually the same thing as having a separate /home partition?  Or, would it be better just to start from scratch and save only things I need (images, documents, etc) and transfer them from a saved backup gradually, as I need them?

Thanks - and I'll probably use the same method when edgy finally is released as finished, so if anything, this is good practice.

---

### Post by mssever on 2006-09-07
You can backup to a FAT partition, but you lose your permissions and any symlinks. If it's your home directory, this probably won't be terrible. But a better way, if you have or can make the disk space, is to make a tarball as follows:
```
cd /home
tar -cjvf myfiles.tar.bz2 yourhomedir
``` You can safely store this tarball anywhere. If it's too big to fit on a FAT filesystem (I think the limit is 2GB), then do
```
split -b 1024m myfiles.tar.bz2
``` and copy the resulting files.

To restore, do the following:
```
#only do this first command if you split the tarball
cat /path/to/split/dir/myfiles.tar.bz2* > /home/myfiles.tar.bz2
tar -xjvf myfiles.tar.bz2
```

---

### Post by henok on 2006-09-12
I think we need a solution to this. I have seen this problem from many people but there doesn't seem to be any solution.

When asked to shutdown it goes to "Will Now Halt" and screen goes blank but power remains on.

I have heard there is an acpi code we can copy and paste to solve this but never actually seen it described.

ANYONE WHO HAS SOLVED THIS, PLEASE HELP!

---

### Post by mssever on 2006-09-13
> **henok said:**
> I think we need a solution to this. I have seen this problem from many people but there doesn't seem to be any solution.

When asked to shutdown it goes to "Will Now Halt" and screen goes blank but power remains on.

I have heard there is an acpi code we can copy and paste to solve this but never actually seen it described.

ANYONE WHO HAS SOLVED THIS, PLEASE HELP!
My systems all work fine, so I can't help you.

You will notice that power management and backups are two completely different issues, so if you hope to get an answer, you should either ask in a related thread or start a new one of your own. No one reading the subject line of this thread will know that you want to know about power management.

---

### Post by sirlancelot on 2006-09-13
> **mssever said:**
> You can backup to a FAT partition, but you lose your permissions and any symlinks. If it's your home directory, this probably won't be terrible. But a better way, if you have or can make the disk space, is to make a tarball as follows:Does creating a tarball preserve permissions and symlinks if/when extracted back to a ext filesystem?

---

### Post by mssever on 2006-09-13
I'm 99% sure that it does. You could test if with fake data to find out...

---

