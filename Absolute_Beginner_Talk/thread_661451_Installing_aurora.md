---
title: "Installing aurora"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2008-01-07
[http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438](http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438)

I extract the folder, cd to the directory and enter

stephen@stephen:~/Desktop/a/aurora-1.3$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
[B]configure: error: C compiler cannot create executables
See `config.log' for more details.[/B]
stephen@stephen:~/Desktop/a/aurora-1.3$ 

but it obviously doesn't work. Any help?

---

### Post by doorknob60 on 2008-01-07
do you have build-essential installed? try this: ```
sudo apt-get install build-essential
``` and try again.

---

