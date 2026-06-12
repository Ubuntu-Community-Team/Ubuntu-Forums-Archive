---
title: "trouble installing clearworks"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by markder on 2006-04-04
I'm having a problem installing the clearworks 0.6.2 theme and engine. This is the error I get. 

```
mark@ubuntu:~/stuff/clearlooks-0.6.2$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... Invalid configuration `i686-pc-linux-oldld': machine `i686-pc-linux' not recognized
configure: error: /bin/sh ./config.sub i686-pc-linux-oldld failed

```

Is the clearworks that comes with breezy the latest version?

---

### Post by Sef on 2006-04-04
Did u install build-essential?    sudo apt-get install build-essential

---

### Post by markder on 2006-04-04
Thanks, that helped a bit but now I can't figure out how to install/upgrade my GTK engine. I hate the search tool on these forums.

edit: 
I get the following error, even though I do have gtk2 installed (I think because sudo apt-get install gtk2-engine-industrial and smooth both said that they were already installed):

checking for gtk+-2.0 >= 2.0.0... configure: error: GTK+-2.0 is required to compile clearlooks-engine

---

