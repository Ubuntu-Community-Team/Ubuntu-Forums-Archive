---
title: "\usr\bin at command prompt"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by iancvt55 on 2008-01-05
I opened a terminal and find myself at ian@Vulcan607:~$ which I presume is like c:\windows at a dos prompt.

No I'm trying to run ./hamachi-init

The Hamachi app I can see in /usr/bin if I use gksudo nautilus and navigate to it but the README for Hamachi says I must run the app from the command prompt.

So how do I get to /usr/bin at the command prompt?

Thanks

Ian

---

### Post by kestrel1 on 2008-01-05
Open the terminal & type:
```
cd /
```
Then:
```
cd /usr/bin
```

---

### Post by lloyd_b on 2008-01-05
> **iancvt55 said:**
> I opened a terminal and find myself at ian@Vulcan607:~$ which I presume is like c:\windows at a dos prompt.

No I'm trying to run ./hamachi-init

The Hamachi app I can see in /usr/bin if I use gksudo nautilus and navigate to it but the README for Hamachi says I must run the app from the command prompt.

So how do I get to /usr/bin at the command prompt?

Thanks

Ian

First, the literal answer to the question: At the command prompt:```
cd /usr/bin
```

Second - you shouldn't even have to do this.  Unless your machine is oddly configured, "/usr/bin" is defined in your "PATH".  If so, then simply typing the command name (without the preceeding "./", which tells the shell to look for the file in the current directory) should do the trick.

You can double-check your PATH with the following command:```
echo $PATH
```

Lloyd B.

---

