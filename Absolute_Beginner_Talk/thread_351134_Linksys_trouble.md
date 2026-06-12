---
title: "Linksys trouble"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by ewkewk on 2007-02-01
I am totally new to this Linux stuff, but am trying to see if I am compatible with this operating system.  I am currently trying to install my Linksys wireless ethernet adapter.  My son who loves Debian could not get it to install on my computer.  It is a new Gigabyte GA-965P-DQ6  based system.  He could get Ubuntu to install and I am anxious to try it.  However, after I extracted the files into the rt2400-1.2.2-b3 folder, when I run make there are a large number of errors "No such file or directory" and then, of course, make install won't run: ***Missing file: System.map.  Probably multiple other files are also missing.  I did run make as root

---

### Post by n8bounds on 2007-02-25
You are trying to manually compile the driver...?

I can assume you already have the build-essential package...you are sure your current working directory contains the make file and whatever else its complaining about?  Can you prove it to yourself?

---

