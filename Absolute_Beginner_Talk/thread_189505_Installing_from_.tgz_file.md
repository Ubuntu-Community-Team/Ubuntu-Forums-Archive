---
title: "Installing from .tgz file"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by obzone on 2006-06-05
I am trying to install Xcircuit from a .tgz downloaded file.

I know it should be straightforward but ..

Where do I store it? I have uncompressed it in a folder on the home directory (below users folder) so that it will be available to all users.

When I try to configure It ( using sudo) it halts because it can't find gcc or equivalent.  Is this not part of the distro and if not where should I get a copy and how important is the version?

---

### Post by Sutekh on 2006-06-05
This link should set you straight on compiling from source / tar.gz, as well as installing the GNU C compiler (gcc)

[http://psychocats.net/ubuntu/installingsoftware.php]("http://psychocats.net/ubuntu/installingsoftware.php")

Section 4 is what you need.

---

### Post by obzone on 2006-06-06
The link provided was very useful:

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

I realise now that the applications I want to load  require certain programs available and enabled:

tcl8.4, tk8.4, gcc, make    - I know these are available and are activated using the instructions from the above link

They also need: 

tcl8.4-dev, tk8.4-dev, libxp, g++, nasm, m4 and Xaw

How do I check if they are available and active and where do I get them if they are not there?

---

### Post by bruce89 on 2006-06-06
Xcircuit is already in the repostories, just enable the universe repository - [http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php) and install Xcircuit with Synaptic.

---

