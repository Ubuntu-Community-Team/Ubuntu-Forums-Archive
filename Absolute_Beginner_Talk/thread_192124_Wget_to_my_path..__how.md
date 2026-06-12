---
title: "Wget to my path..  how?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-06-08
Hi,

How do I wget to a path I choose? I want the download to be downloaded to /media/sda1/

How do I do that with wget?

Thanks

EDIT:

I found out. I just needed to cd to the folder first.

cd /media/sda1/
Wget [www.theurl.com/thefile](www.theurl.com/thefile)

---

### Post by asimon on 2006-06-08
Yes, wget saves the file by default into your current directory, which you can switch with cd. Another way is to use
```

wget -P /media/sda1/ www.theurl.com/thefile

```
saves thefile under /media/sda1 no matter what your current directory is.

---

