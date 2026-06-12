---
title: "puting together a tar ball"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-07
I have been given a a url to make a tar ball from all the files 
is there an application that does this or is it a matter of copy and paste
ith the touch command.
url is

[url]http://svn.noreply.org/svn/mixmaster/trunk/Mix/

---

### Post by kont.raen on 2006-03-07
[QUOTE=lex1]I have been given a a url to make a tar ball from all the files 
is there an application that does this or is it a matter of copy and paste
ith the touch command.
url is

[http://svn.noreply.org/svn/mixmaster/trunk/Mix/](http://svn.noreply.org/svn/mixmaster/trunk/Mix/)[/QUOTE]

First of all - as the files you want to put into the tar-archive aren't on your own filesystem - you'll need to download them via wget. If wget is not installed on your machine, just go and install it via synaptics. Then open up a terminal and do as follows :

1. create a new subdirectory for the files you download from the server and chdir there
```
mkdir /tmp/download
cd /tmp/download
```

2. fetch the files from the server
```
wget --recursive --level=inf http://svn.noreply.org/svn/mixmaster/trunk/Mix/
```

3. create the tarball
```
tar cvfz /tmp/tarball.tar.gz ./
```

---

