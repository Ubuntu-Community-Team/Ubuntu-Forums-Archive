---
title: "apt-get can not find file java6u5 in desktop"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by harryliddic on 2008-03-22
installing jre-6u5-linux.bin from desktop has been a chore. I got information on what to do once apt-get finds the file, but on its its own or with  the path apt-get returns can not find file.

---

### Post by Bachstelze on 2008-03-22
BIN files have nothing to do with Apt. Please be more specific about what you wish to install and how.

---

### Post by forestpixie on 2008-03-22
I don't know that apt-get will know what to do witha .bin file - it deals with .deb files.

To install a bin file you need to give it permission to run as an executable with chmod a+x and then ./ it, don't know that it's a good idea to run it from the desktop. I moved mine into my /home before I dealt with it previously.

---

### Post by bruce89 on 2008-03-22
To install the JRE, issue

```
sudo aptitude install sun-java6-jre
```

Executing a bin file is asking for upgrade trouble when the time comes.

---

### Post by harryliddic on 2008-03-22
a simple question. how do I move the file from desktop to home?

---

### Post by bruce89 on 2008-03-22
> **harryliddic said:**
> a simple question. how do I move the file from desktop to home?

You can drag it around if you open a file manager window showing your home folder.

```
mv old_location new_location
```

is the CLI way.

---

### Post by harryliddic on 2008-03-22
The simple ways are often the hardest to figure out. I appreciate your two answers to my post.



thanks a lot!

---

