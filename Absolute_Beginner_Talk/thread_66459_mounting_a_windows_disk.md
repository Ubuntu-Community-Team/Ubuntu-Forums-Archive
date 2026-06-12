---
title: "mounting a windows disk"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-09-17
Hi, i dont know if i can do this bui it would be really nice.

My machine has 2 hard disks one with linux one with windows.
I already use thunderbird on my win pc and would like to access the disk from ubuntu, so all my local folders is always in the same place.

I guess what im asking is - Is it possible to read an NTFS formatted disk from linux I can see the disk under the system >admin>disks but i cannot seem to enable it.

---

### Post by xmastree on 2005-09-17
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

You can read an ntfs disk, but you can't write to it with linux.

---

### Post by dgrafix on 2005-09-17
what about the other way round? That article also mentions FAT, is this old FAT or FAT32?

Also can someone tell me what sudo means, as the commands seem to work with or without it

---

### Post by xmastree on 2005-09-17
> what about the other way round?Write but not read?
Fat32 is best for sharing data between windows and linux as both systems can read and write it.
> Also can someone tell me what sudo means```
man sudo
``` It's for running commands as another user, root by default. You'll be asked for the password the first time, but not for a while as it has a timeout. Root has greater privelidges than a regular user.

For example, try running:
```
gedit /etc/X11/xorg.conf
``` It'll open, but you'll notice it says read only at the top. This is because a regular user can't write to this file. Putting sudo before the command will allow you to write the file. (So don't do it...)

---

### Post by aysiu on 2005-09-17
[QUOTE=dgrafix]
Also can someone tell me what sudo means, as the commands seem to work with or without it[/QUOTE] [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

