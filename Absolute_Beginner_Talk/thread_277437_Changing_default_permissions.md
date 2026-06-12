---
title: "Changing default permissions"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by opticsnake on 2006-10-14
How do I change the default permissions for a shell?  I'm creating scripts as I learn unix and I'm tired of having to run chmod everytime I create a new script.  My current umask is set at 22 (octal).:-?

---

### Post by taurus on 2006-10-14
You can set that, umask=022, in ~/.bashrc...

---

### Post by opticsnake on 2006-10-14
> **taurus said:**
> You can set that, umask=022, in ~/.bashrc...

I guess maybe I must have misspoken myself.  My current default permissions are -rw-rw-rw- which the umask changes to -rw-r--r--  I would like my default permissions to be -rwxrw-rw-

Anyone know how to change it?

---

