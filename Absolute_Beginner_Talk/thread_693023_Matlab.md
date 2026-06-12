---
title: "Matlab"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by confused! on 2008-02-10
Trying to install matlab R2007a into ubuntu 7.10 --- not getting far. The manual says make a directory and go to it as so:
[I]
cd /usr/local
mkdir matlab74_sv
cd matlab74_sv[/I]

It wouldn't let me at first until I stuck sudo in front of mkdir,

but when it comes to the next line:

*/dvd/install_unix.sh*

...it just tells me where I can shove my installation with:

[I]bash: /dvd/install_unix.sh: No such file or directory
[/I]

Though this seems odd as the file is definitely there. However, it seems I'm not allowed to toy with it --- am I not  a user with Linux' equivalent of Win Administrator status? Which seems odd if I'm the only one who uses it.

---

### Post by spiderbatdad on 2008-02-10
you are the administrator of you home directory...linux protects the system's file system from accidental damage by requiring either root login or super user privileges...it's an extra step that provides security and protection.
Is the binary file in the directory you created? Has it been unpacked? Then I would assume you would run the command from within the folder /dvd/install_unix.sh in the directory /usr/local/matlab74_sv/dvd/install_unix.sh

you can login in as root with **sudo su**

---

### Post by amd-64 on 2008-02-19
Do you have a /dvd folder. In my installation, Gutsy, my dvd drive is mounted to /media/cdrom use a file manager to search for the name of the dvd drive or type mount at a command line.

---

