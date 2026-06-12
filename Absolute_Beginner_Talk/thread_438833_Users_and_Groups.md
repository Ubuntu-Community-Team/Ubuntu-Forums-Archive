---
title: "Users and Groups"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by CFD on 2007-05-10
I'm just setting up Ubuntu and created two users and I'm encountering a few problems.. :confused: 

When switching users the screen goes blank with a white rectangle in the top left

When trying to change users permissions the admin application tries to start but stays as a blank window...very strange. starting this from the terminal with sudo users-admin does the same thing with nothing reported in the terminal window.

Has anyone come across this or any bright ideas?

Thanks

---

### Post by vinmar on 2007-05-10
You could try

gksudo strace users-admin

Won't fix it, but might help work out what's wrong.

---

### Post by Austin_KW on 2007-05-10
When switching users, see if an new display has been created on vitrual terminal 8,9,10 with 'ctrl-alt-F8,F9 etc.

---

### Post by CFD on 2007-05-12
tried "gksudo strace users-admin" and found lots of possible errors, but no clue what they all mean...

access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
...
read(3, 0xbfe49a6c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
...

Looks like some important files are missing possibly.

---

