---
title: "How do I delete a protected folder from my desktop?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-24
Please see attachment. I want to delete the AdobeReader file entirely.  I appreciate any assistance in accomplishing this task.
kh

---

### Post by meney on 2007-04-24
Open up a terminal

```
cd Desktop
sudo rm -R AdobeReader
```

I think that sould work?

---

### Post by kittyhawk63 on 2007-04-24
> **meney said:**
> Open up a terminal

```
cd Desktop
sudo rm -R AdobeReader
```I think that sould work?

Fantastic! Makes my day.

Thanks

---

### Post by meney on 2007-04-24
No problem :D

---

### Post by marko_4454 on 2007-04-24
Yea, meney is right. Whats happening is that you are not the owner, but rather root is the owner, so you cannot delete that unless you are "sudo" thats why meney put the "sudo" part in a command that most of the time will not have it.
The -R is just a flag meaning to remove recursively.

---

### Post by kittyhawk63 on 2007-04-24
> **marko_4454 said:**
> Yea, meney is right. Whats happening is that you are not the owner, but rather root is the owner, so you cannot delete that unless you are "sudo" thats why meney put the "sudo" part in a command that most of the time will not have it.
The -R is just a flag meaning to remove recursively.

marko_4454,
Thanks for the added information.
kh

---

### Post by nolan- on 2007-04-26
Excellent, that was bugging me too.
Thanks :)

---

