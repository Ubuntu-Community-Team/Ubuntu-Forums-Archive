---
title: "Bootstrap dependency Problems"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by tgbrowning on 2007-08-01
Have a problem with dependencies and can't figure out how to fix it.  Looking in the bootstrap.log, I see the following:

Selecting previously deselected package base-files.
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_4ubuntu2_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.11_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you request:
 base-passwd depends on libc6 (>= 2.3.4-1); however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.11) ...

dpkg: base-files: dependency problems, but configuring anyway as you request:
 base-files depends on awk; however:
  Package awk is not installed.
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not installed.
Setting up base-files (4ubuntu2) ...

TSelecting previously deselected package base-files.
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_4ubuntu2_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.11_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you request:
 base-passwd depends on libc6 (>= 2.3.4-1); however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.11) ...

dpkg: base-files: dependency problems, but configuring anyway as you request:
 base-files depends on awk; however:
  Package awk is not installed.
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not installed.
Setting up base-files (4ubuntu2) ...
hSelecting previously deselected package base-files.
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_4ubuntu2_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.11_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you request:
 base-passwd depends on libc6 (>= 2.3.4-1); however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.11) ...

dpkg: base-files: dependency problems, but configuring anyway as you request:
 base-files depends on awk; however:
  Package awk is not installed.
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not installed.
Setting up base-files (4ubuntu2) ...

There's more, but it's much the same thing. My guess is that I need to uninstall a bunch of things until I can reinstall the correct libpam-modules. What are my options? Any quick and clean way to do this?

Browning>>>

---

### Post by apswartz on 2007-08-04
You got some very basic packages missing! What exactly are you doing? It looks like you are trying to create a "linux from scratch."

---

### Post by swoll1980 on 2007-08-04
sudo apt-get install -f " That should fix dependencies

---

### Post by tgbrowning on 2007-08-06
Elucidate, please?   I've been picking and choosing here and there and feelling my way around -- I guess you could say I'm experimenting quite a bit.  

What wonderous things am I missing?

---

### Post by tgbrowning on 2007-08-06
Well, I'm kind of mystified.  I ran :

sudo apt-get install --fix-broken 

and 

Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
browning@browning-laptop:~$ 

This stuff was at the top of the file.  How long ago would it have been. I made a probably stupid assumption that the boot-strap.log file would be new with each booting. Maybe that's not the case.  The whole file is 679 lines long.

The Date modified field shows it to be last modified (?) on 04/07/07.

Is it just an old log file that means nothing?

Browning>>>

---

### Post by apswartz on 2007-08-06
```
sudo apt-get install libc6 awk libpam-modules
```

You still have said what exactly you are trying to do.

---

