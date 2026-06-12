---
title: "installing man files"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-11-11
I installed my Java from java.sun.com using the .bin file and extracted to /usr/lib/Java6u3/ and made the symbolic links to /usr/bin for the executables in the bin directory using update-alternatives however, I can't figure out where to put the man pages contained in the Java6u3/man directory? According to the manpath.config file in /etc, /usr/bin PATH is linked to /usr/share/man but what command do I use to do the actual copying? Here is the result of ls -al of the man directory:

noorez@noorez-laptop:/usr/lib/Java6u3/man$ ls -al
total 16
drwxr-xr-x  4 root root 4096 2007-10-29 17:18 .
drwxr-xr-x 11 root root 4096 2007-10-29 17:18 ..
lrwxrwxrwx  1 root root   11 2007-10-29 17:18 ja -> ja_JP.eucJP
drwxr-xr-x  3 root root 4096 2007-10-29 17:18 ja_JP.eucJP
drwxr-xr-x  2 root root 4096 2007-10-29 17:18 man1

---

### Post by bakeneko on 2007-11-11
sudo cp -ir /usr/lib/Java6u3/man/* /usr/share/man
See **man cp** for more information about copying files on the command line.
You can also use **gksudo nautilus** (or your favorite file manager) to get a privileged browser that can move/copy files anywhere, just be careful and don't leave it open.

---

### Post by noorez on 2007-11-12
Thanks, that worked.
Just another sort of related question: 
I found a similar problem to what I had, and it was solved using cpio and not cp. According to man pages, cpio is used for archives, so why use it for copying non archive files?

---

### Post by bakeneko on 2007-11-12
In addition to copying to/from archives, **cpio** is useful for copying symlinks and hardlinks. If you are copying a directory tree with such links and want to make sure they are copied as links, you can use cpio in a fashion similar to this:
```
$ cd /usr/lib/Java6u3/man
$ find . -print0|sudo cpio -0pvd /usr/share/man
```
Rather than having a recursive mode, **cpio** operates on a list of files, which can be supplied with **find**. Here, it is important to **cd** first so that **find** will produce a file listing relative to **/usr/lib/Java6u3/man**.  In the next command, **.**, the current directory, will be **/usr/lib/Java6u3/man**. The **-print0** option to find and the **-0** option to cpio tell these commands to use a list of files separated by null characters instead of newlines, so that even files with newlines in their names will be copied. **-p** tells cpio to operate in pass-through mode (copy from directory to directory instead of creating an archive.) **-v** is for verbose output, and **-d** tells cpio to create directories as needed.

---

