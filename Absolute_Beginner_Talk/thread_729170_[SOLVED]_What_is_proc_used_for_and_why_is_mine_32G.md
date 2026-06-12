---
title: "[SOLVED] What is /proc used for and why is mine 32GB?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-19
I don't have much hard drive space left, so I'm trying to get rid of some unnecessary data. What is /proc used for and why is it using 32GB of my hard drive space?

---

### Post by Daveth on 2008-03-19
"5.1. A Virtual File System

Under Linux, all data are stored as files. Most users are familiar with the two primary types of files: text and binary. But the /proc/ directory contains another type of file called a virtual file. It is for this reason that /proc/ is often referred to as a virtual file system.

These virtual files have unique qualities. Most of them are listed as zero bytes in size and yet when one is viewed, it can contain a large amount of information. In addition, most of the time and date settings on virtual files reflect the current time and date, indicative of the fact they are constantly updated."

In other words, it isn't really there!!! Spooky, eh?

---

### Post by Wiifreak on 2008-03-19
[http://en.wikipedia.org/wiki/Procfs](http://en.wikipedia.org/wiki/Procfs)

Very important file system 

> On Unix-like computer systems, procfs, short for process file system, is a pseudo-file system (pseudo in that it is dynamically generated at boot) used to access process information from the kernel. The file system is often mounted at the /proc directory.** Because /proc is not a real file system, it consumes no storage space and only a limited amount of memory.**

Looks something is wrong with it...
I don't know if it's an option, but have you tried to repair your distro?
So only the filesystem will be repaired.
I don't know for sure if this can be done safely.
Is there an expert who know if this can be done?

---

### Post by tszanon on 2008-03-19
My suggestion: don't touch /proc.
As said before, it stores important information about important things, and it's not stored in your hard drive. It's stored in memory.

---

### Post by whoscheesemine on 2008-03-19
Okay, thanks! This thread contains everything I needed to know! Solved.

---

