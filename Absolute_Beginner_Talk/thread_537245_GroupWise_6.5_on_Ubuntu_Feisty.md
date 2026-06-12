---
title: "GroupWise 6.5 on Ubuntu Feisty"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ciclonauta on 2007-08-28
Hi there, 
I downloaded from novell's web site the package "gw656up1lnxm.tar.gz", that it suppose to run on linux. When I uncompress it and run the installer (./install), I have the following output:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
./install.sh: 7: rpm: not found
./install.sh: 8: rpm: not found
[: 32: 3: unexpected operator
[: 32: 1: unexpected operator
Traceback (most recent call last):
  File "install.py", line 2, in ?
    import frontend, sys
  File "frontend.py", line 2, in ?
  File "/home/marco/downloads/gwinst/python/lib/python2.2/lib-tk/Tkinter.py", line 35, in ?
    import _tkinter # If this fails your Python may not be configured for Tk
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory

Does anybody have an idea??

---

### Post by jamvegan on 2007-08-28
I don't know anything about most of those errors, but if the last line of the traceback is the root of the problem it looks like a failed dependency.  If you have libtiff.so.4 installed (as do I), you could try creating a symlink to try to trick the installer.  If 4 is sufficiently backwards compatible that would work (I'd say this trick has worked for me slightly more often than not when encountering this sort of problem).
```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

---

### Post by ramjet_1953 on 2007-08-29
Have you already installed [COLOR="Blue"]build-essential[/COLOR] ?

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

This is necessary for compiling from source code.

Also, do you understand that when compiling from source code, you usually need to satisfy dependencies manually?

Again, when compiling, you not only need the dependent packages, but the development package associated with it.

Compiling is not something that is generally recommended for those new to Linux, as it can be extremely frustrating, without a knowledge of what is going on.

Regards,
Roger 8)

---

### Post by ciclonauta on 2007-08-31
hi there, first of all thanks you for your response.
At first step I saw my installed packages and I have just installed the "build-essencial" package, so in second place I made the simlink to the library as jamvegan says, once I made it, I checked again with the installer

> ./install

And got similar error, but with other library, so after made the folliwing links a setup window appeared:

sudo ln -s /usr/lib/librpm-4.4.so /usr/lib/librpm-4.2.so
sudo ln -s /usr/lib/librpmbuild-4.4.so /usr/lib/librpmbuild-4.2.so
sudo ln -s /usr/lib/librpmdb-4.4.so /usr/lib/librpmdb-4.2.so
sudo ln -s /usr/lib/librpmio-4.4.so /usr/lib/librpmio-4.2.so

But when I choose to install the Group Wise Client, appears another window with the following error:

Install failed for an unknow reason (27)

While in the virtual terminal window I obtain the following output:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
./install.sh: 7: rpm: not found
./install.sh: 8: rpm: not found
[: 32: 3: unexpected operator
[: 32: 1: unexpected operator

Any idea??
thanks you very much for your help

---

