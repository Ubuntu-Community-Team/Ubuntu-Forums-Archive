---
title: "Why can't cd command see the directory?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-11
I don't know why I am having so much trouble getting this command line down but I am.

Here is an example of my problem.

dace@dace-desktop:~$ ls -l
total 1745296
-rw-r--r-- 1 root root          0 2007-06-07 10:03 1
-rw-r--r-- 1 dace dace     255544 2007-06-07 09:50 automatix2_1.1-4.5-7.04feisty_i386.deb
-rw-r--r-- 1 root root 1785144650 2007-06-10 11:06 backup.tgz.old
drwxr-xr-x 2 dace dace       4096 2007-06-09 10:05 Desktop
drwxr-xr-x 2 dace dace       4096 2007-06-07 21:24 Documents
lrwxrwxrwx 1 dace dace         26 2007-06-07 08:02 Examples -> /usr/share/example-content
drwxr-xr-x 2 dace dace       4096 2007-06-11 16:13 Linuxstuff
-rw-r--r-- 1 root root          2 2007-06-11 07:13 resolv.conf
-rw-r--r-- 1 dace dace         16 2007-06-11 07:38 test
-rw-r--r-- 1 dace dace          9 2007-06-11 07:36 test~
dace@dace-desktop:~$ 
dace@dace-desktop:~$ 
dace@dace-desktop:~$ cd  /linuxstuff
bash: cd: /linuxstuff: No such file or directory
dace@dace-desktop:~$

I know that this is trivial but I can't seem to get it.

---

### Post by taurus on 2007-06-11
There is no /linuxstuff.  I think you mean Linuxstuff--~/Linuxstuff.

```
cd Linuxstuff
ls -la
```

---

### Post by ICUR2Ys on 2007-06-11
Yes, I see.  I knew it would be something simple like this, but I just couldn't see it.

Thank you very much.

---

### Post by Lord Illidan on 2007-06-11
The / is the root folder, kinda like the C: directory in Windows. Thus, when you typed /Linuxstuff, you were referring to a folder in the root directory /, not in the home directory.

If you were already in the home directory, you could have typed cd Linuxstuff.

---

### Post by ICUR2Ys on 2007-06-11
Thank you for your response.  I have finally been able to get a script file to run.  So I guess I am making some progress with this command line.

I really appreciate your help

---

### Post by pppetter on 2007-06-11
plus filenames are case sensitive in unix/linux

---

