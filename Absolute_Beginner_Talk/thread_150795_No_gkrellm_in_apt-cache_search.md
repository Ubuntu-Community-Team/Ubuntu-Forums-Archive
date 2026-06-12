---
title: "No gkrellm in apt-cache search?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by jtp51 on 2006-03-26
I am surprised that gkrellm isn't listed when I run:

sudo apt-cache search gkrellm

I've tried different search strings with no success either. Therefore gkrellem is only installed manually?

Thanks,

---

### Post by gord on 2006-03-26
you need to make sure you [ enable extra repositorys](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)
then do a ```
 sudo apt-get update 
```
and try again :)

---

### Post by Xian on 2006-03-26
It's in the Universe repo for Breezy and Dapper:

```
sudo apt-cache policy gkrellm
Password:
gkrellm:
  Installed: (none)
  Candidate: 2.2.7-5ubuntu1
  Version table:
     2.2.7-5ubuntu1 0
        500 http://us.archive.ubuntu.com dapper/universe Packages
```

---

### Post by jtp51 on 2006-03-26
$ sudo apt-cache policy gkrellm
W: Unable to locate package gkrellm
$ sudo apt-cache search gkrellm
$

As of this evening, 9:33PM CST, gkrellm is not there.

I had already ran sudo apt-get update.

Thanks,

---

