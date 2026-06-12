---
title: "x64 limewire"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-11
Hello!

Is it possible to download limewire on a x64 system architecture and get it to work?

I converted the default download from .rpm to .deb using alien and have just used this code:

```


sudo dpkg -i LimeWire-free_4.12.6_i386.deb


```

with the following result:

> 

dpkg: error processing LimeWire-free_4.12.6_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 LimeWire-free_4.12.6_i386.deb



Thanks!

---

### Post by Frak on 2006-10-11
Trust me an easier and better program is frostwire, a clone of limewire, it installs on x64 arch. in a breeze.

---

### Post by blendmaster on 2006-10-11
Sorry, wrong error!

Here's the right one:

> 

dpkg-split: error reading LimeWire-free-4.12.6: Is a directory
dpkg: error processing LimeWire-free-4.12.6 (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 LimeWire-free-4.12.6
grant@Grant:~/Desktop$



---

### Post by blendmaster on 2006-10-11
Is frostwire an exact clone?

---

### Post by skymt on 2006-10-11
Frostwire is an exact clone. It's based on the same source, but it's a community project and has somewhat better Linux support.

---

### Post by blendmaster on 2006-10-11
Okay, I'll use it instead.

Had I known an open-source alternative existed, I wouldn't have even touched LimeWire.

---

### Post by blendmaster on 2006-10-11
Yep!

It's awesome!

---

