---
title: "sudo has died - how to fix"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by sdgreen on 2007-06-28
For some reason my ability as user to su sudo has died. Hence I cannot initiate any program that needs root access. 

I get this error

sdgreen@sdgreen-desktop:~$ sudo
sudo: /etc/sudoers is mode 0660, should be 0440
sdgreen@sdgreen-desktop:~$ 

How does one fix this?

---

### Post by chandler on 2007-06-28
try ```
chmod 440 /etc/sudoers
```

Looks like you should have permission to, and it's just spitting out a warning

If this doesn't work on the local machine you'll have to use the liveCD as a rescue CD and do it from there after you mount the partition...

---

### Post by Rocket2DMn on 2007-06-28
Something wrong with the file permissions on the sudoers binary perhaps?  If you can't chmod it to 440 (since you can't sudo), try doing it from nautilus.

---

### Post by chandler on 2007-06-28
If that doesn't work then he has read and write and could copy the file, rm the old one and mv the old to /etc/sudoers  and chmod 440 and he'll have ownership of the new file as well..  he'll have to change that afterwards though.

---

### Post by tuxcantfly on 2007-06-28
since sudo won't work, you'll have to boot into "recovery mode" (from grub), or boot a livecd and mount your partition, and run this command:

```
chmod 440 /etc/sudoers
```

---

### Post by sdgreen on 2007-06-28
Thanks. Changing to recovery mode and running the chmod command appears to have fixed the problem.

This forum Rocks !!!!

---

### Post by speaker219 on 2007-06-28
> **sdgreen said:**
> Thanks. Changing to recovery mode and running the chmod command appears to have fixed the problem.

This forum Rocks !!!!
By Jove, I think he's got it!

---

