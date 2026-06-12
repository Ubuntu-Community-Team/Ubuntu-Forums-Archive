---
title: "[SOLVED] application install question"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by offroad64 on 2007-12-25
When installing an application for example Azureus in which folder does the program reside on my hard drive ? or any programs for that matter:confused:

---

### Post by taurus on 2007-12-25
The binaries are usually resided in /usr/bin and it should be in your path so you can run those apps anytime and anywhere.

Applications -> Accessories -> Terminal
```
ls /usr/bin
```

---

### Post by Hospadar on 2007-12-25
Linux doesn't group files by program, it goes by type of file, executables in one folder (/usr/bin usually) libraries in another (/usr/lib or /lib) manpages in another, and then configuration files live in your home directory usually.  If you need to know what files are installed you can get it through the command line with aptitue (apt-get) although I'm not sure exactly how, or much easier, go to System-Administration->Synaptic then find the package you want to know about, right click->Properties->Installed files.

If it's something you built yourself, it might be anywhere, but most developers use standard locations for their makefiles, so look in /bin, /lib /usr/bin, /usr/lib, /usr/local/bin, etc.   Also if you go to places and go to "Find Files" (or "Search"?) you can usually just search the packages name (or a distinctive part of it) and find what you're looking for.

---

### Post by offroad64 on 2007-12-25
Thank you all I needed to know

---

