---
title: "[SOLVED] Looking for file locations in Ubuntu Gutsy?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2007-10-21
I'm trying to locate the host files to edit userplane chat to get rid of the adds. The file in a windows OS is located at
 > C:/Windows/system32/drivers/etc/hosts
or
> C:/WINNT/system32/drivers/etc/hosts

Where would i find these files in Ubuntu Gutsy?

I've looked in etc/hosts and found a few other files/folders named "hosts" but none with data that needs editing...Thanks...

---

### Post by ezak on 2007-10-21
The equivalent to the C:/Windows/system32/drivers/etc/hosts file in Windows is in /etc/ directory named "hosts" in Ubuntu and in almost all Linux distros.

There is no other main hosts file you need to edit.

---

### Post by e1ektrob0y on 2007-10-21
Ok i found that file, now i can't edit it because i do not own the file and i can't change permissions...How do i do that? CHMOD or something right?

---

### Post by Maestro23 on 2007-10-21
> **e1ektrob0y said:**
> Ok i found that file, now i can't edit it because i do not own the file and i can't change permissions...How do i do that? CHMOD or something right?

It' owned by root.  You need root permission.  The sudo command is what you need for terminal commands.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you want to edit the file, you can use the gedit text editor.

> gksudo gedit /etc/hosts

---

### Post by ezak on 2007-10-21
No, CHMOD won't do you any good since you do not need your username ownership of the file to edit it.

You need sudo (super user) access to the file, since it is a system file.

Simply type " sudo gedit /etc/hosts " in a terminal to edit the file directly and save when you are finished, or you can type " sudo nautilus " in a terminal and navigate to /etc/hosts file and edit with the editor of your choice by right-clicking and choosing a editor. However you prefer. ;-)

---

### Post by e1ektrob0y on 2007-10-21
Thanks:D done...

---

