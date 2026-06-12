---
title: "How do I give myself permissions to this mount?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Mark Raymond on 2007-06-18
I have a Windows network, which I can mount using this:

sudo mount //192.168.2.3/Mark /home/markr/mydocs

However, my user (markr) only has read permissions once it is mounted - when it's not mounted, everyone has complete permissions to /home/markr/mydocs. However, once mounted, I can only read. What do I do?

---

### Post by dmond on 2007-06-18
try using the chmod.
type:

sudo chmod 777 -R /the_mounted_directory

---

### Post by aktiwers on 2007-06-18
Isnt that something you have you have to do from the Windows Computer?
Allow Read/write.

---

### Post by fdrake on 2007-06-18
.....

---

### Post by dreadlord_chris on 2007-06-18
> **Mark Raymond said:**
> I have a Windows network, which I can mount using this:

sudo mount //192.168.2.3/Mark /home/markr/mydocs

However, my user (markr) only has read permissions once it is mounted - when it's not mounted, everyone has complete permissions to /home/markr/mydocs. However, once mounted, I can only read. What do I do?

check your permission in Windows for that share...

---

### Post by dreadlord_chris on 2007-06-18
> **dmond said:**
> try using the chmod.
type:

sudo chmod 777 -R /the_mounted_directory

That won't work here - you can't apply *nix permissions to Windows filesystems

---

