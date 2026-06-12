---
title: "How to run apps from CD"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by jso2897 on 2006-11-16
I don't know how to run an app from a cd rom. I have no idea how to get to any directories (like those on a CDrom) outside of the file system. Cab anybody help me?

---

### Post by CatKiller on 2006-11-16
If the thing you're trying to run is a Linux application, then it should come with instructions on how to run it. If it's a Windows application, then you'll have to use [Wine]("http://www.winehq.com/"), or something similar.

You can't access a directory that isn't part of your filesystem. Everything to do with your computer is treated as a file in the filesystem. [Mounting]("http://en.wikipedia.org/wiki/Mount_%28computing%29") is the process of putting something in the filesystem. Your cdrom **should** be mounted automatically when you put it in the drive, with an icon appearing on the desktop. /cdrom in your directory structure is usually a link to where the cdrom is mounted.

I hope this helps.

---

### Post by jso2897 on 2006-11-16
Thank you! That works! :D

---

