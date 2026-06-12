---
title: "Question"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Th3Futur3 on 2006-08-21
Ive tried to install a source file and have i type in sudo make install a bunch of things happen but nothing happens, just a bunch of icons on my desktop. I dont know what do from here

---

### Post by taurus on 2006-08-21
What are you trying to install?  I assume you know you can take a snapshot of your desktop if you can't explain what happens.  Then, people would know what's the problem from your screenshit!!!

---

### Post by Th3Futur3 on 2006-08-21
Ok I put an attachment of my desktop.

---

### Post by taurus on 2006-08-21
Did you unpack it in ~/Desktop?  Change to that directory and see it...

```
cd ~/Desktop
ls -la
```

---

### Post by Th3Futur3 on 2006-08-21
Here is what I got when i typed in the code

alex@alex-linux:~/Desktop$ ls -la
total 2264
drwx------  9 alex alex    4096 2006-08-21 17:55 .
drwxr-xr-x 31 alex alex    4096 2006-08-21 18:56 ..
-rw-r--r--  1 alex alex    2430 2006-08-21 15:58 config.h
-rw-r--r--  1 alex alex   39529 2006-08-21 17:55 config.log
-rwxr-xr-x  1 alex alex   39144 2006-08-21 17:55 config.status
drwxr-xr-x  2 alex alex    4096 2006-08-21 17:55 data
drwxr-xr-x  3 alex alex    4096 2006-08-21 17:55 doc
drwxr-xr-x  4 alex alex    4096 2006-08-21 17:55 goocanvas
drwxr-xr-x  8 alex alex    4096 2006-07-30 15:41 gpredict-0.5.99.7
-rw-r--r--  1 alex alex 1779870 2006-08-20 13:45 gpredict-0.5.99.7.tar.gz
-rwxr-xr-x  1 alex alex   22491 2006-08-21 15:58 intltool-extract
-rwxr-xr-x  1 alex alex   35212 2006-08-21 15:58 intltool-merge
-rwxr-xr-x  1 alex alex   28068 2006-08-21 15:58 intltool-update
-rwxr-xr-x  1 alex alex  217307 2006-08-21 17:54 libtool
-rw-r--r--  1 alex alex   24513 2006-08-21 17:55 Makefile
drwxr-xr-x  4 alex alex    4096 2006-08-21 17:55 pixmaps
drwxr-xr-x  2 alex alex    4096 2006-08-21 17:55 po
-rw-r--r--  1 alex alex   57972 2006-08-20 14:25 pyRadar-0.4.tar.gz
drwxr-xr-x  5 alex alex    4096 2006-08-21 17:55 src
-rw-r--r--  1 alex alex      23 2006-08-21 17:55 stamp-h1

---

### Post by taurus on 2006-08-21
> **Th3Futur3 said:**
> Here is what I got when i typed in the code

alex@alex-linux:~/Desktop$ ls -la
total 2264
drwx------  9 alex alex    4096 2006-08-21 17:55 .
drwxr-xr-x 31 alex alex    4096 2006-08-21 18:56 ..
-rw-r--r--  1 alex alex    2430 2006-08-21 15:58 config.h
-rw-r--r--  1 alex alex   39529 2006-08-21 17:55 config.log
-rwxr-xr-x  1 alex alex   39144 2006-08-21 17:55 config.status
drwxr-xr-x  2 alex alex    4096 2006-08-21 17:55 data
drwxr-xr-x  3 alex alex    4096 2006-08-21 17:55 doc
drwxr-xr-x  4 alex alex    4096 2006-08-21 17:55 goocanvas
drwxr-xr-x  8 alex alex    4096 2006-07-30 15:41 gpredict-0.5.99.7
-rw-r--r--  1 alex alex 1779870 2006-08-20 13:45 gpredict-0.5.99.7.tar.gz
-rwxr-xr-x  1 alex alex   22491 2006-08-21 15:58 intltool-extract
-rwxr-xr-x  1 alex alex   35212 2006-08-21 15:58 intltool-merge
-rwxr-xr-x  1 alex alex   28068 2006-08-21 15:58 intltool-update
-rwxr-xr-x  1 alex alex  217307 2006-08-21 17:54 libtool
-rw-r--r--  1 alex alex   24513 2006-08-21 17:55 Makefile
drwxr-xr-x  4 alex alex    4096 2006-08-21 17:55 pixmaps
drwxr-xr-x  2 alex alex    4096 2006-08-21 17:55 po
-rw-r--r--  1 alex alex   57972 2006-08-20 14:25 pyRadar-0.4.tar.gz
drwxr-xr-x  5 alex alex    4096 2006-08-21 17:55 src
-rw-r--r--  1 alex alex      23 2006-08-21 17:55 stamp-h1

Recognize those names somewhere?  They are exactly the same with those icons on your desktop!!!  So if you remove them from ~/Desktop, they will disappear.  Otherwise, move them somewhere else like ~/temp...

---

### Post by Th3Futur3 on 2006-08-21
I know there on my desktop but I was asking why. I typed in make install into the terminal and all those icons came on my desktop but the program is not installed.

---

### Post by Th3Futur3 on 2006-08-21
Ok i finally found what is wrong. My make file is messed up. This is what i get in terminal.

config.status: WARNING:  ../gpredict-0.5.99.7/goocanvas/po/Makefile.in.in seems to ignore the --datarootdir setting

How can I fix that?

---

