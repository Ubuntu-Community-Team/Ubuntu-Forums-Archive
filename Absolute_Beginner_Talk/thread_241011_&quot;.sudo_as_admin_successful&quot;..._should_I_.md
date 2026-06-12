---
title: "&quot;.sudo_as_admin_successful&quot;... should I be paranoid?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by tefflox on 2006-08-21
what is this file?  does this mean somebody cracked my system?

---

### Post by Ragazzo on 2006-08-21
If it doesn't exist, you will get a help message when you start up a terminal how to use sudo.

---

### Post by NetworkGuy on 2006-08-21
I also have the same file.   I don't think your system has been hacked.

---

### Post by breno leitao on 2008-04-04
This is just a flag that bash check to see if it is your first time as a sudoer. 
I also think this is ubuntu specifically. 

Breno

---

### Post by Oldsoldier2003 on 2008-04-04
> **breno leitao said:**
> This is just a flag that bash check to see if it is your first time as a sudoer. 
I also think this is ubuntu specifically. 

Breno

yup delete it and then run bash:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
```
 after running sudo the file will be created and no more banner.

---

### Post by tefflox on 2008-04-05
Thanks !!

It is all sufficient for me to not give a damn !

:lolflag:

---

