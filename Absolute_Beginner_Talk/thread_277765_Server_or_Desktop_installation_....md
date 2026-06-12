---
title: "Server or Desktop installation ..."
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Andy from Somerset on 2006-10-15
I have two PC's connected by a wireless router. I want to install Ubuntu on 'client' PC but leave the 'server' as Windows (for the time being). If I download the Desktop version, should that work ok? Basically all I need to do on the 'client' is access the Internet and some of the files on the 'server'. Presumably I will need to download the relevent Linux drivers for the wireless adapter. The router is a dlink DSL-G604T

Thanks

---

### Post by mejy on 2006-10-15
> **Andy from Somerset said:**
> I have two PC's connected by a wireless router. I want to install Ubuntu on 'client' PC but leave the 'server' as Windows (for the time being). If I download the Desktop version, should that work ok? Basically all I need to do on the 'client' is access the Internet and some of the files on the 'server'. Presumably I will need to download the relevent Linux drivers for the wireless adapter. The router is a dlink DSL-G604T

Thanks

An Ubuntu install should have no problem accessing files on a windows box through 'samba' - search around and there are plenty of tutorials on how to do so.

Unless you are running a web server and are experienced with Linux, you should go with the Desktop version.  The server is simply a cut down desktop install (without a Graphical Interface and desktop apps) with an optimized kernel for computers with lots of RAM and many processors.

As for your wireless adapter, the changes are you'll want to look into ndiswrapper.

---

### Post by TheWizzard on 2006-10-15
i agree with mejy
if you want to use the command line only the server version is ok. otherwise you should use a desktop version. you can always stop the graphical interface later if you want to save resources.

---

### Post by Andy from Somerset on 2006-10-16
Many thanks

---

