---
title: "is linux like unix?"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by querent on 2007-01-27
I'm trying to start learning about computers...i have a begingers book on unix...and have been led to believe linux is based on unix.  is this true?  are there differences that would be comprehensible to a newbie?  will a beginers book on unix be helpfull?  where is a good reference for linux commands?  

q

---

### Post by Tomosaur on 2007-01-27
Linux is indeed based upon Unix. The full name is GNU/Linux, GNU being a recursive acronym, meaning 'Gnu's Not Unix' :D

If you're familiar with Unix, then Linux will not be a big shock to your system.

A good Linux command reference is the [Linux In A Nutshell command line reference](http://www.oreillynet.com/linux/cmd/) from O'Reilly.

The default shell in Ubuntu is BASH, which means 'Bourne Again Shell' (Bourne was a Unix shell).

---

### Post by 23meg on 2007-01-27
> and have been led to believe linux is based on unix. is this true?Linux is a kernel, whereas Unix is a whole operating system. However, Linux based operating systems are generally referred to as "Unix-like", which is accurate, since the same general userspace tools as in Unix, or clones of them, are used in these (including Ubuntu).

---

### Post by jrusso2 on 2007-01-27
Actually Linux is not based on Unix. It is a Unix like operation system that is based on unix principals.

Linus Torvalds the developer of the Linux kernel was a college student who could not afford a powerful operating system to run on his 386.

He looked it minix but found it lacking.  He could not afford Unix which was very expensive at the time.

So he thought I am this hot shot coder why don't I design my own and Linux was born.

Jeanette

---

### Post by 23meg on 2007-01-27
Yes, it's more accurate to say Unix was a big influence on Linux.
[QUOTE=Tomosaur]The default shell in Ubuntu is BASH,[/QUOTE]It was changed to DASH in Edgy; the change is mostly transparent to the user though.

---

### Post by Tomosaur on 2007-01-27
> **23meg said:**
> Yes, it's more accurate to say Unix was a big influence on Linux.
It was changed to DASH in Edgy; the change is mostly transparent to the user though.

Woah, really? I've been running Edgy for ages now, very transparent indeed!

Anyway yes, Linux is not actually 'derived' from Unix, it's just Unix like. I find it easier to just call it 'based on' though.

---

### Post by PurplePenguin on 2007-01-27
As soon as I read that dash replaced bash, I wondered why.  So I did a bit of searching.  In case you're as curious as I am, here's what I found from the [ubuntu wiki]("https://wiki.ubuntu.com/DashAsBinSh"):

> Summary

Change the /bin/sh symlink on Ubuntu systems to point to the dash shell instead of the current bash shell.

Rationale

Our default shell is currently bash, which is slow and very large as it is intended as a user login shell. While this is good for users, it is not the best shell for running shell scripts; there are far smaller and faster shells that provide POSIX compliance such as dash.

By changing the /bin/sh symlink from bash to dash we can have the best of both worlds.

Use cases

   * Matthias is a software developer of an application whose shell configure script is very long, dash is able to execute it orders of magnitude faster than bash. (OpenOffice.org's configure scripts runs two and a half minutes quicker).
    * Jane is a user whose old laptop takes a long time to boot, dash is able to execute the shell init scripts much faster than bash. (The boot is 30s faster).
    * Lianne is developing an embedded system with low memory and space requirements, Ubuntu is a more attractive base as it uses a 79K shell binary instead of a 649K one.


---

### Post by deadgobby on 2007-01-27
You can use Unix commands in Linux.
Gobby

---

### Post by IYY on 2007-01-27
Pretty much everything you learn from your Unix book you will be able to use in Linux. Then, it would be a good idea to pick up an advanced Linux or even Debian book and learn newer, Linux-specific administration and package management commands.

---

