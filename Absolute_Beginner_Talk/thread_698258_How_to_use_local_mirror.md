---
title: "How to use local mirror"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by G33 on 2008-02-16
My ISP has a local Ubuntu mirror.

It is not listed, How do i set it up to use the IPS's local mirror?

---

### Post by PeterJS on 2008-02-16
Do you know that address of the mirror?

You can manually edit the sources list with:
```

gksudo gedit /etc/apt/sources.list

```
And replace all of the references to the main servers with your local server.

---

### Post by G33 on 2008-02-16
there are a lot to change.

how do i know if it worked?

---

### Post by PeterJS on 2008-02-16
If after you change it you can successfully run
```

sudo apt-get update

```
Then it's working.

---

