---
title: "Application path?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by niceguy123 on 2007-09-16
How do I figure out what the path is to an application?

---

### Post by theredcross on 2007-09-16
```
locate application
```
where "application" is what you are looking for. Most likely it will be in /usr/bin

/usr/bin holds executable paths, what in particular do you need to find from the application?

---

### Post by vambo on 2007-09-16
```
which <app_name>
```

---

### Post by cmnorton on 2007-09-16
which <application-name>

which tells you the application your PATH currently points to.

which -a finds call copies if there is more than one of the same name.

---

### Post by niceguy123 on 2007-09-16
I'm trying to configure FireFTP to open PHP files with Bulefish. What I haven't figured out is what should I put in the path line here.

---

### Post by Hospadar on 2007-09-16
What I always do is open synaptic, find the package in question and right click and go to properties->installed files and look for the file that has the same name as the command you would use to open the program from the command line.  it's generally in /usr/bin or /usr/lib if it's a dynamic library.  probably for bluefish it's going to be something like /usr/bin/bluefish

using "which" will work just great for finding the executable as well.  the method I described is more for when you need to hunt down other package files.

---

### Post by Delkster on 2007-09-16
> **niceguy123 said:**
> I'm trying to configure FireFTP to open PHP files with Bulefish. What I haven't figured out is what should I put in the path line here.

Depends on how you installed this Bluefish. I assume what you want is the path to the executable file.

In Linux, when you install applications using the package manager, the executables usually go to /usr/bin, shared libraries (comparable to .dll files in Windows) go mostly to /usr/lib, other files potentially shared with other applications such as images go to /usr/share, configuration files go to /etc, and so on. All files of a single application do not go to a single path.

So, if you installed Bluefish using the Ubuntu tools, the executable is most like in /usr/bin.

On the other hand, if you install software from a third-party site, it may well go to /opt, and the entire application may be placed in the same path under /opt. Or it might go somewhere else depending on how the application was packaged.

---

