---
title: "mxmlc: Permission denied"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by rbarrett on 2007-11-02
Hi guys,

I made the flex 2 sdk into a package and installed it.  Everything seems OK except I can't seem to run the MXML Complier.  When I try 'sudo mxmlc xxx.mxml' I get a "Permission denied" message.  

Any thoughts on how to get the compiler to work?

---

### Post by Partyboi2 on 2007-11-02
What does the permissions for the file say?
```
ls -l (*file*)
```
Have you tried changing file permission for it?

---

### Post by tarchy on 2007-11-02
This will give you temporary root permissions:

```

sudo -s -H 

```

---

### Post by rbarrett on 2007-11-03
Thanks.  I simply had to change the permissions on the file.  Love it when it's a simple solution.

---

