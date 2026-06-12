---
title: "how to use tar.gz"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-11-14
hey all,

I was wondering how to install stuff once you have the tar.gz file (im trying to grab superkaramba for ubuntu)

thanks

---

### Post by poudin on 2007-11-14
tar -zxvf to extract the archive...there is 2 compressions in effect

then check the new folder for a README or similar instructions.

---

### Post by mike^_^ on 2007-11-14
To unpack/unzip
```
tar -zxvf filename.tar.gz
```
As far as the installation goes, you should check the README or INSTALL file included with the program.  Installing/compiling from source is usually done by:

```
./configure
```
```
make
```
```
sudo make install
```

---

### Post by JasonBourneLinux on 2007-11-14
with sudo make install do I just navigate to the unpacked files (but which file do I navigate to)

---

### Post by aysiu on 2007-11-15
You haven't tried grabbing SuperKaramba by [enabling extra repositories](http://www.psychocats.net/ubuntu/sources) and then pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
sudo apt-get update && sudo apt-get install superkaramba
``` In other words, why do you need a .tar.gz file at all?

---

### Post by JasonBourneLinux on 2007-11-15
good point-thanks

---

