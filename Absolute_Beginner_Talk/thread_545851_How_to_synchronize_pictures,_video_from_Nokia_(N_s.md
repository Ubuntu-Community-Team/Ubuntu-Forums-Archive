---
title: "How to synchronize pictures, video from Nokia (N series) phone to ubuntu"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by arai on 2007-09-08
How to get the pictures, video from Nokia (N series) phone to ubuntu. The software commonly used is Nokia PC Suite.

---

### Post by Ek0nomik on 2007-09-08
I would suggest you try bitpim.  It's done wonders for my LG phones.

---

### Post by arai on 2007-09-08
the description in Synaptic Package Manager says

> bitpim - utility to communicate with many CDMA phones.

but the nokia phone i use doesn't use  CDMA. It uses GSM.

---

### Post by schorsch on 2007-09-08
Please take a look [here]("http://ubuntuforums.org/showthread.php?t=468900") ....

---

### Post by arai on 2007-09-08
that thread doesn't have a solution yet.

---

### Post by schorsch on 2007-09-08
If you read all the pages you will see that you are able to copy files via the Obex FTP java frontend to your phone and back. Well, it is not really syncing but better than nothing .....

---

### Post by arai on 2007-09-08
I tried to install obexftp-frontend and got the following response. 

```
usrnme@usrnme-desktop:~/Desktop/obexftp-frontend-0.6.2-bin$ chmod 755 Run.sh
usrnme@usrnme-desktop:~/Desktop/obexftp-frontend-0.6.2-bin$ ./Run.sh
Exception in thread "main" java.lang.ClassFormatError: net.sourceforge.obexftpfrontend.Main (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at java.security.SecureClassLoader.defineClass(libgcj.so.70)
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)
usrnme@usrnme-desktop:~/Desktop/obexftp-frontend-0.6.2-bin$ 
```How do I proceed now? I don't know if it is installed or not yet.

---

### Post by schorsch on 2007-09-08
Which java verson are you using?
```
java -version
```

---

### Post by arai on 2007-09-08
Here is the output for  "java - version"

```
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

