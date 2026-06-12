---
title: "Users *reading* each others files"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by optimal on 2008-03-18
Hi everyone!

Been using Ubuntu for a few months now and I must say that I really enjoy using it! But Linux users (*edit: not the people / contributors, but rather the system privilege type*) have still got me stumped! Let me explain my predicament;

I live in a flat with a few people and we all share my computer, we each have our own user, and as such our own music, videos and pictures. Currently we can't access each others stuff which is a shame for sharing our entertainment!

So we've all agreed that we have no secrets to hide, but would rather our work wasn't broken, is there a way so that we have Read, Write, Execute privileges on our own files, but also to have Read on all files. Chmod, Chown, Users and Groups is all latin to me so I need a little help if anyone could oblige me! Kudos to y'all!

---

### Post by billgoldberg on 2008-03-18
> **optimal said:**
> Hi everyone!

Been using Ubuntu for a few months now and I must say that I really enjoy using it! But Linux users (*edit: not the people / contributors, but rather the system privilege type*) have still got me stumped! Let me explain my predicament;

I live in a flat with a few people and we all share my computer, we each have our own user, and as such our own music, videos and pictures. Currently we can't access each others stuff which is a shame for sharing our entertainment!

So we've all agreed that we have no secrets to hide, but would rather our work wasn't broken, is there a way so that we have Read, Write, Execute privileges on our own files, but also to have Read on all files. Chmod, Chown, Users and Groups is all latin to me so I need a little help if anyone could oblige me! Kudos to y'all!

Save the files you want to share (music, movies, ...) on a 2nd partition, that way everyone can access them.

If you have the admin password you can also read all files from all users.

---

### Post by Paqman on 2008-03-18
A shared partition sounds like a good solution, but giving everybody read access of each other's home directory would probably mean less disruption to your users.

If you don't want to use the CLI and chown, then you can just use nautilus. You'll need to run it as root, so launch it with 
```
gksudo nautilus
``` 
Go to the users' folders within /home, right click, go to permissions and change it so that "others" have read permission. Make sure you check the wee box for applying the change to files/folders within the directory. Job done.

---

### Post by scramasax on 2008-03-18
> **optimal said:**
> ... is there a way so that we have Read, Write, Execute privileges on our own files, but also to have Read on all files.

And "execute"? ...

Don't mark a file as "x" if it you don't know it needs to be executable.  That's a security hazard -- not a great one but one, nonetheless.

Permissions seem confusing at first inasmuch as "r" is read, "w" is write, but "x" is execute or "traverse".  Executable files must be set to "x" if they are to run, but a directory ("folder") must be set to "x" if someone is to have access to it.

You don't have to do anything to have everyone have "Read on all files" -- if by "all files" you mean all documents you create in your home area.  They're automatically created as rw-r--r--.

In other words, they're created with read/write for you, read-only for your group, and read-only for anyone else.

So if  that's what you want, there's nothing to do.

---

### Post by Xiong Chiamiov on 2008-03-18
It seems that maybe it's the actual sharing between machines you need help with?  If that's the case, sharing between Linux machines you should use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo"), and with Windows you [need]("https://help.ubuntu.com/community/SettingUpSamba") [Samba]("http://ubuntuforums.org/showthread.php?t=202605").

---

### Post by Paqman on 2008-03-19
> **Xiong Chiamiov said:**
> It seems that maybe it's the actual sharing between machines you need help with?  If that's the case, sharing between Linux machines you should use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo"), and with Windows you [need]("https://help.ubuntu.com/community/SettingUpSamba") [Samba]("http://ubuntuforums.org/showthread.php?t=202605").

It's just a single machine, with multiple users.

---

