---
title: "Mounting osx partition and Shell prompt"
date: 2007-04-29
forum: Apple PPC Users
---

### Post by tomos on 2007-04-29
My Ubuntu shell prompt was username:~$.

I attempted to mount my osx partition with:

sudo mkdir /mnt/macosx
sudo /sbin/parted

(parted) print
(parted) quit

sudo mount -t hfsplus /dev/hda3 /mnt/macosx

cd /mnt/macosx

The mac partition did not mount and
what I got was a new shell prompt:  

username@username-pb4:~$

where username-pb4 is my macosx shell prompt?  

Somehow I've got apples and oranges side by side.

---

### Post by tomos on 2007-04-30
Issue settled with help from users list.  Removing "@\h" from PS1 in ~/.bashrc fixed the prompt.

---

