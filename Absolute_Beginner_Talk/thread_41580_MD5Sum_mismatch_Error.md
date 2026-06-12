---
title: "MD5Sum mismatch Error"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by czambran on 2005-06-14
Why do I get this errors when I try to download some packages through synaptic? It has hapenned with several packages. Is it because I actived the backport repositories?

---

### Post by Seth on 2005-06-14
[QUOTE=czambran]Why do I get this errors when I try to download some packages through synaptic? It has hapenned with several packages. Is is because I actived the backport repositories?[/QUOTE]
 Hi czambran,

The US/CA archive is currently experiencing issues. To fix this, open a Terminal and issue the command:

**sudo gedit /etc/apt/sources.list**

And change all lines with [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) to [http://archive.ubuntu.com](http://archive.ubuntu.com)

Note that you just remove the "us." :-D

Have a great day!

---

### Post by bosshoff on 2005-06-14
Yes, that works all well and good unless you're installing dependencies via apt-get, it's already downloaded stuff from the US server, then it fails at some file way down the line.  How do we delete the files that have already been downloaded, and, what is so hard about making sure a server has the correct files?

EDIT: NVM, just forgot to apt-get update

so, remember, do that too  ;-)

---

### Post by czambran on 2005-06-14
That fixed all my problems. I now have php5 on my machine.

Thanks.

Christian

---

