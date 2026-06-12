---
title: "virtual environment"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by noppeli on 2007-05-23
i seaching for answer how can i building full virtual environment from freeware software.
one idea is use ubuntu feisty and xen but is this best resolve.

if i use example hp blade server and vmware esx this is good idea but cost a lot.
please help me and find right way.
sorry my bad english language :)

---

### Post by jbrown96 on 2007-05-23
I don't use virtualization, but from what I have heard, Feisty has very good options. After installing feisty, get a program called automatix. It has two virtualization programs for free: VMware and I can't remember the other. They are both free, so there worth a try.

---

### Post by veloce on 2007-05-24
> **noppeli said:**
> i seaching for answer how can i building full virtual environment from freeware software.
one idea is use ubuntu feisty and xen but is this best resolve.

if i use example hp blade server and vmware esx this is good idea but cost a lot.
please help me and find right way.
sorry my bad english language :)

vmware server is in the **Commercial** Feisty repository.  It's not esx, but it's very good for free software.

---

### Post by noppeli on 2007-05-24
thanks for you help.

I just install feisty and vmware server.
i wonder is openmosix good software to do ha cluster

---

### Post by veloce on 2007-05-24
> **noppeli said:**
> thanks for you help.

I just install feisty and vmware server.
i wonder is openmosix good software to do ha cluster

I set up a virtual openmosix cluster but, as I didn't really have anything that could use it, never got very far on the testing.  I had hoped to be able to set up vmware under openmosix, but I understnd that a vm gets treated as one process so the load is not shared around the cluster.

---

