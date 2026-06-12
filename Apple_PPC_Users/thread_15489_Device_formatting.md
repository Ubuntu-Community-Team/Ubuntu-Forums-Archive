---
title: "Device formatting"
date: 2005-02-14
forum: Apple PPC Users
---

### Post by dubdubdub on 2005-02-14
Is there an application similiar to disk copy (for OS X) that will allow me to view drives, repair permissions and format them.

I am simply trying to format a 128mb flash stick.

Thanks in advance

---

### Post by evangelion on 2005-02-14
I haven't used Disk Copy before,  but an ok gui partition program is qtparted, available via apt-get,  but since you just want to format your flash stick I'd just put it in, unmount it,  and;
```

sudo mkdosfs -F 32 /dev/sda1

```
This will format it with a fat32 filesystem (which is what it was originally formated with), which I don't think understands permissions anyway so you don't have to worry about that.

---

