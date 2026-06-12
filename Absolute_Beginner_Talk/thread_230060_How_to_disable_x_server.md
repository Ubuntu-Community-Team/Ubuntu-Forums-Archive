---
title: "How to disable x server"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by FireJin3 on 2006-08-05
Hi, obviously I'm very new to linux and would like to install the current nvidia driver on my system. In order to do that I need to turn off x server, which I don't see how I would do.

Thank you for any help.

---

### Post by Titus A Duxass on 2006-08-05
The easiest way of install the nvidia drivers is with Automatix or easyubuntu.

---

### Post by MrHorus on 2006-08-05
> **FireJin3 said:**
> Hi, obviously I'm very new to linux and would like to install the current nvidia driver on my system. In order to do that I need to turn off x server, which I don't see how I would do.

Thank you for any help.

```
sudo telinit 3
```

Will switch to runlevel 3 and will shut down the X server.

Then you can install the NVidia driver and then telinit 5 to boot it back up or startx.

---

### Post by jtgamma on 2006-08-05
You just pres

```
Ctrl+Alt+Backspace
```

:D

---

### Post by tseliot on 2006-08-05
Follow my guide about installing the Nvidia driver:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by Stevman on 2006-08-05
I think that's restart, but also 
# sudo /etc/init.d/gdm stop 
to stop gdm works.(or start to start :) )

---

### Post by MrHorus on 2006-08-05
> **jtgamma said:**
> You just pres

```
Ctrl+Alt+Backspace
```

:D

That merely restarts it, not shuts it down,

---

### Post by FireJin3 on 2006-08-05
Thanks guys, I seemed to have made it work, although with some trouble.

---

### Post by Perkins on 2006-08-06
<ctrl><alt><bkspace> *does* shut it down.

<ctrl><alt><shift><bkspace> restarts it.

However, I believe that with the default setup, X is being run by gdm, so when you kill it, gdm sees that it's dead and resurrects it.  So you either need to switch to a lower runlevel, or kill gdm.  Instructions for both are posted above.

I know this may seem like a trivial distinction, but with Linux such details can be important.  For example, if your system doesn't use gdm or its equivalent, then X doesn't come back when you use <ctrl><alt><bkspace> and you would be wise to make sure you know how to restart it before doing so.

---

### Post by qsz on 2006-08-10
Hi!

As I'm having same kind of a problem I thought I could as well post here. I'm trying to install Nvidia drivers but X server is causing problems. I tried to turn it off on many ways, sudo /etc/init.d/gdm stop worked. Then I got more problems:

> Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC test with CC="cc".
-> gcc-version-check failed:
   
   ./usr/src/nv/conftest.sh: line 19: cc: command not found
   
   Could not compile gcc-version-check.c.  Please be sure you have your distrib
   ution's libc development package installed and that 'cc' is a valid C compil
   er name.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: Yes)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


Any ideas what does that mean?

---

### Post by qsz on 2006-08-11
Any ideas?

---

### Post by krymphus on 2007-12-23
I am having this same problem if someone could give a reason it would be great. Please Help

---

### Post by SOULRiDER on 2007-12-23
> **tseliot said:**
> Follow my guide about installing the Nvidia driver:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

Follow his directions. Installing software on Linux can be much easier than in windows.

---

