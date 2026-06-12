---
title: "Failed to execute child process &quot;xmms&quot; (no such file or directory)."
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by newlinuxuser on 2006-02-25
I dontloaded stream tuner using Automatix but when I try to listen to stations i get the error message "Failed to execute child process "xmms" (no such file or directory)." - ooo another quick question, I installed Opera using Automatix aswel but  cant find it, I used find/search files and all menus :-k  any help would be greate:)

---

### Post by cilynx on 2006-02-25
It's looking for "xmms" which is a common audio player.  You need to install xmms.  I assume you can do this via Automatix, but I don't know as I've never used Automatix personally.

To install xmms from the command line:

```

sudo apt-get install xmms

```

I don't think I can help you with Opera.  Check if you can run 'opera' on the command line.

---

### Post by Sydius on 2008-05-24
I know this thread is old, but I'm having the same problem.  When I tried to do "apt-get install xmms" I got the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
```

---

### Post by 43moon on 2008-05-25
> **Sydius said:**
> I know this thread is old, but I'm having the same problem.

Me too.  It was installed before I upgraded but now it is gone...

---

### Post by LinuxRocks713 on 2008-05-30
```
$ sudo apt-get install xmms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

```

Trying to install xmms in Ubuntu 8.04

---

