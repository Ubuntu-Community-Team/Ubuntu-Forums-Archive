---
title: "The &quot;.d&quot; ending in directory names"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by jrjazzman on 2006-11-08
What does the ".d" ending in some system directory names indicate?

I've wondered this for a while, but I can't find a search tool that understands ".d" as a keyword.

---

### Post by po0f on 2006-11-08
jrjazzman,

It means it's a directory.  Look in /etc, there is probably a file called /etc/modprobe.conf and a directory called /etc/modprobe.conf.d/.  Since you can't have two files with the same name, a ".d" is appended to the directory.

---

### Post by jrjazzman on 2006-11-08
> **po0f said:**
> 
It means it's a directory.  Look in /etc, there is probably a file called /etc/modprobe.conf and a directory called /etc/modprobe.conf.d/.  Since you can't have two files with the same name, a ".d" is appended to the directory.

ahh.. probably should have been able to deduce that.  So, why would /etc/modprodbe.conf not be more like /etc/modprobe/modprobe.conf?  Did it start out as only one file needed, then later more files necessitated a separate sub-directory?

---

### Post by po0f on 2006-11-08
jrjazzman,

I believe you can put everything in modprobe.conf, but the file on some people's systems was quite big, so they switched to the modprobe.conf.d/ directory, where all entries in there are IIRC combined automatically for you into modprobe.conf.  Plus, something like this probably happened:

Guy #1:  We need a directory to store configuration files for modprobe.conf.
Guy #2:  `mkdir /etc/modp<hits tab>.d`  There.

---

