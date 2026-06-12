---
title: "home dmrc folder being ignored"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-03-12
yep i have done it again ,i have been trying a lot of how to's to fix it but it does not want to work,
i dont want to reinstall ,

there must be a fix out there that is simple and works

thank you

---

### Post by qpwoeiruty on 2007-03-12
:confused: :confused: :confused: 

I've no idea what your problem is by your description. Have you chown'd it and made sure it has appropriate permissions? Sorry if this isn't the solution to your problem but I just can't figure it out. What exactly is the problem?

---

### Post by STREETURCHINE on 2007-03-12
as the title says 

users $home file is being ignored.this prevents the default session and language from being saved 
permissions.users $home directory must be owned by user and not writable by outhers

---

### Post by qpwoeiruty on 2007-03-12
Try this:

chown -R $(whoami) /home/$(whoami)
chmod 644 /home/$(whoami)
chmod 644 /home/$(whoami)/.dmrc

---

### Post by STREETURCHINE on 2007-03-12
```
chown -R $(whoami) /home/$(whoami)
``` this comes up with missing operand



```
chmod 644 /home/$(whoami)
``` 


```
chmod 644 /home/$(whoami)/.dmrc
``` this comes up with no such file or directory


it looks like i may have deleted that but i dont know how it was all fine till the power went out last night and when i rebooted this morning this is what i faced

---

