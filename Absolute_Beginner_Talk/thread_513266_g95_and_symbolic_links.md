---
title: "g95 and symbolic links"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by castep_nut on 2007-07-30
I've been trying to install a fortran compiler called g95 from [http://g95.sourceforge.net/](http://g95.sourceforge.net/)

The installation instructions simply suggest downloading the tar file and extracting:

"This will create a directory named 'g95-install' in the current directory. Run (or better yet make an appropriate symbolic link) to ./g95-install/bin/i686-pc-linux-gnu-g95 in order to run g95. "

However, the file will not run, and any attempt to create s symbolic link to the usr/bin fails on the grounds of denied permission (despite the fact that I have opened all files and folders to read and write)

Has anyone successfully managed to install g95?

Thanks

---

### Post by asmoore82 on 2007-07-30
you should always be installing stuff via apt/synaptic when available.

if you have to install from a 3rd party source and want to install it systemwide you will
have to install it with root priviledge.

I believe the standard GNU C compiler gcc is capable of processing Fortran.

---

### Post by castep_nut on 2007-07-30
Annoyingly this is programme that definitely requries this g95 compiler. 

Isn't it quite dangerous to login as root? I thought ubuntu didn't like that (hence the sudo command)?

---

### Post by alvenegas on 2007-09-15
There is a Debian package that you can get by editing the /etc/apt/sources.list
The website is here:
[http://www.gfd-dennou.org/library/cc-env/g95/index.htm.en](http://www.gfd-dennou.org/library/cc-env/g95/index.htm.en)

Now, it does  not work fully, as I have tried to run it and I suppose is missing a link
to file f951 on the library directory.

---

