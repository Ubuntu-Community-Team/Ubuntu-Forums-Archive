---
title: "[SOLVED] java intall difficulty"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by goldencj on 2007-12-25
tlc@tlc-desktop:~$ chmod a+x jre-6u2-linux-i586-rpm.bin
chmod: cannot access `jre-6u2-linux-i586-rpm.bin': No such file or directory
tlc@tlc-desktop:~$

---

### Post by rkd on 2007-12-25
Just a wild guess, but did the installation instructions tell you to change into the directory created when you extracted the files from the tar file BEFORE entering that chmod command?

---

### Post by Sef on 2007-12-25
If you just want to install java, this is the easy way to do it:

Applications > Add/Remove > Change top right box to 'All Available Applications' > search (type in "Sun Java 6") > Click on the top option > Apply > Apply > OK

---

### Post by goldencj on 2007-12-25
Thanks for the help u2!

---

### Post by Sef on 2007-12-25
> jre-6u2-linux-i586-rpm.bin

That's a rpm and Ubuntu use .deb.  To make it work, read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

