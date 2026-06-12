---
title: "[SOLVED] Java Virtual Machine issues"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2007-09-27
i'm trying to install JAlbum. i downloaded the bin file and now when i run "sh JAlbuminstall.bin" it gives me:
```
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.
```

i'm more than sure that JVM is installed, this is /etc/jvm:

```
# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr

```

and this is how my PATH looks like:
```

/usr/lib:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

```

---

### Post by mendingo84 on 2007-09-27
i forgot to 
```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by tszanon on 2007-09-27
What happens when you type this in the terminal:
```
java -version
```
Two things came to mind:
1. JAlbum isn't finding the JVM;
2. The JVM it's finding is obsolete for it.

Edit: nevermind. You solved it by yourself while I was typing. :)

---

