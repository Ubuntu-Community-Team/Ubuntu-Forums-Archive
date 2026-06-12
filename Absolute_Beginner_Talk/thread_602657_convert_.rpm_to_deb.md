---
title: "convert .rpm to deb"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Velosiped on 2007-11-04
Hi

I am trying to convert .rpm package to deb with alien, but every time I got answer that "filename.rpm" not found. but it exists in my home catalog. could anyone say what's the problem?

here is my  example from terminal window:

administraator@ubuntu:~$ sudo alien -c cndrvcups-capt-1.30-1.i386.rpm
File "cndrvcups-capt-1.30-1.i386.rpm" not found.

---

### Post by taurus on 2007-11-04
Maybe because you saved it to ~/Desktop!

```
cd ~/Desktop
```

---

### Post by por100pre1 on 2007-11-04
Welcome to the forums. Try typing:

```
sudo alien -c 
```

with a space after it, drag and drop the file into the "terminal" window and *THEN* press Enter.

---

### Post by Velosiped on 2007-11-04
thanx both of you. of course I saved it to the desktop:)  but everything is ok now thanx to you and .deb packages have succesfully created,

---

### Post by poision_heart on 2007-11-04
You must ve to specify path of file then only alien ll install your rpm.

---

