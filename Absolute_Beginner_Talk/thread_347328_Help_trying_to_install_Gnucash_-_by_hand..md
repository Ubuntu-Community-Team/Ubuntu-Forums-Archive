---
title: "Help trying to install Gnucash - by hand."
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2007-01-27
Hi,

I'm trying to install the latest version of Gnucash by downloading from Sourceforge.  The version in the repositories is out of date.

This is my first attempt to do anything other than synaptic so please bear with me.

I downloaded the tar.gz file and unpacked it in to my tmp directory.

In to the terminal and cd to tmp directory and then the gnucash directory.  ./configure and it started to configure.  Kept stopping complaining that such and such file was missing.  Went and found the relevant file in Synaptic, downloaded and re-ran ./configure.  After several stops to find missing dependencies I'm now stuck with this message:

[cut]
checking for scm_long_long2num in -lguile... yes
checking if unsigned long is at least as big as guint32... yes
checking if guile needs our copy of srfi-1... no
checking if guile needs our copy of srfi-11... no
checking if guile needs our copy of srfi-19... no
checking if guile needs our copy of srfi-2... no
checking if guile needs our copy of srfi-8... no
checking if guile needs our copy of srfi-9... no
checking if guile needs our copy of (guile www)... checking for guile... (cached) /usr/bin/guile
checking for guile-config... /usr/bin/guile-config
checking for guile-tools... /usr/bin/guile-tools
checking if (www main) is available... no
checking for gconf-2.0 >= "2.0"... Package gconf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gconf-2.0' found
configure: error: Library requirements (gconf-2.0 >= "2.0") not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
ray@ubuntu:/tmp/gnucash-2.0.4$


I'm stumped.  According to Synaptic, I do have gconf-2.0 installed.  It seems to be telling me to move this file somewhere.

Help please :)

---

### Post by an.echte.trilingue on 2007-01-27
you need libgconf2-dev

Also, this is just a suggestion, since this is the first time you compile something, but you should probably install checkinstall.

Then, instead of doing this to install the program:
```
./config
make
make install

```
you do this:
```
.config
checkinstall
```

This leaves you with a .deb that you can install with dpkg, and the real advantage is that this makes your package manager aware of it, so that if the version in the repos gets updated beyond what you have compiled, the program you compiled will be replaced by the one one from the repos.  Also, if you decide you don't want it later on, you can remove it in synaptic, which is much easier than trying to keep track of the ./uninstall script and using it.

To install the .deb that you build this way, 
```
dpkg -i <package_name>
```

---

### Post by Phosphoric on 2007-01-27
OK.... eventually installed all the dependencies and also installed checkinstall.

so... did ./configure
             checkinstall

about 30 minutes later I got this:

[cut]
chown: changing ownership of `/var/tmp/EiooJLpogWkZXWjfSLaNc/package//usr/share/doc/gnucash/doc/misc-notes.txt': Operation not permitted
chown: changing ownership of `/var/tmp/EiooJLpogWkZXWjfSLaNc/package//usr/share/doc/gnucash/doc/Makefile': Operation not permitted
chown: changing ownership of `/var/tmp/EiooJLpogWkZXWjfSLaNc/package//usr/share/doc/gnucash/doc': Operation not permitted
chown: changing ownership of `/var/tmp/EiooJLpogWkZXWjfSLaNc/package//usr/share/doc/gnucash': Operation not permitted

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]: n

Erasing temporary files...OK

Deleting temp dir...OK

ray@ubuntu:/tmp/gnucash-2.0.4$


What have I done wrong this time?

Should I have done: ./configure
                             make
                             checkinstall  ?

Should there be a sudo in there somewhere?


Thanks :)

---

### Post by tonyr1988 on 2007-01-27
Yes, do:

./configure
make
sudo checkinstall

It'll ask you some questions (pretty common-sense) and it'll install it all for you. I think checkinstall is the only one you need sudo for, but not positive.

---

### Post by Phosphoric on 2007-01-27
Thanks for the help folks, I finally have my first hand made package running. :KS 

Couple of questions to round off the very valuable learning experience:

I seem to have installed the package in my tmp directory because that's where the tar.gz file unpacked itself. :confused: 
I would have preferred it to be in my home directory.  Is it possible to move the package, and if so, will future updates via Synaptic find it?

I found out eventually that to start the programme I go in to the terminal and enter "gnucash".

Is there a way to create a desktop shortcut and/or in the drop down applications menu under office where I expected to find it.

Thanks again folks, great learning experience. :D

---

