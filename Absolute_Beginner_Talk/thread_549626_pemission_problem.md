---
title: "pemission problem"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Lelouch on 2007-09-12
i mounted some iso images using terminal:

sudo mount -o -loop -t iso 9660 <dir.iso> <dir>

the problem is that the mounted folders ae read-only... 

i tried to change their permission (chmon a=rwx) or by another ways but i couldn't...

I cant delete these folders..

I am using feisty... with only one user

---

### Post by Celegorm on 2007-09-12
Did you try to unmount them? If not try 'sudo umount /path/to/mountpoint'

edit- my bad, yes, umount does need sudo

---

### Post by diatribe on 2007-09-12
you must use sudo with umount

---

### Post by Lelouch on 2007-09-13
something wrong with the command

sudo: unmount: command not found

---

### Post by hyper_ch on 2007-09-13
Lelouch:

You did not read right... it's not "unmount" but "umount"

---

### Post by Lelouch on 2007-09-13
still not working

/path/to/mountpoint is not mounted... but read-only

---

### Post by Lelouch on 2007-09-13
btw... the same is with Examples folder...


I cant edit it, or change its permission...

And, a lock icon appears on top of these folders

---

### Post by Celegorm on 2007-09-14
> **Lelouch said:**
> i tried to change their permission (chmon a=rwx) or by another ways but i couldn't...

What error did you get? The command is chmod, by the way, and you will need to put 'sudo' in front of it if you don't own the file or folder you are changing permissions on (for example, 'sudo chmod a=rwx /iso/folder'). And even though you are the only user on the system, everything outside of your home directory is probably owned by root.

---

