---
title: "Problems with glib"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by s1k3st on 2006-08-27
I just wanted to install the new version of gaim, but when I ran the configure command it came up with an error about glib not being installed (even though it was).  So I decided to download and install glib.  The installation went smooth.  I finally thought I was going to be able to install gaim, but when I run the configure command now it come's back with an error "'pkg-config --modversion glib-2.0' returned 2.12.2, but GLIB (2.10.3) was found!".  So now what should I do?

---

### Post by simonn on 2006-08-27
If you are compiling something from source (gaim in your case) which requires something (glib in this case) you need to have the dev package installed. 

This is because gaim needs the glib header files so it knows how to build itself against the version of glib you have installed - if that makes sense?

However, installing glib-dev will not solve the complete problem in this case. Gaim requires gtk2.0 which in turn requires glib2.0, so...

```

$ sudo apt-get install libgtk2.0-dev

```

Observe all the packages that are installed. You will get an idea of what gtk2.0 depends on.

---

### Post by s1k3st on 2006-08-27
I tried installing what you said, but sadly it didn't help.  I'm not an expert with linux by any means, but I think the answer provided will not work for me anymore because I took it upon myself to install the new version of glib.  Maybe some of the files from the previous one are still on my system.  My reason for thinking this is the error it returns

```
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.12.2, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

```

So I'm guessing what I want to do is remove the old version (or the new one) right?how?

---

### Post by simonn on 2006-08-27
> **s1k3st said:**
> So I'm guessing what I want to do is remove the old version (or the new one) right?

Yes. 

> how?

What commands did you use to install glib? 

The bit I am really looking for is the --prefix parameter (or lack thereof) to the ./configure step.

If you installed it without a --prefix then it would be installed into /usr/local. This is good.

If you used --prefix=/usr then we will need to take a different approach so that you do not break your running system.

So, if you **DID NOT** use --prefix=/usr follow this.

If you still have the directory where you compiled glib, simply cd into that directory and enter:

```

$ sudo make uninstall

```

If you do not have the source directory, unpack the glib source again and do:

```

$ ./configure [with the exact parameters you used originally]
$ make
$ make uninstall

```

Your system should now be picking up the default glib - which is in /usr. If it still does not work, follow the instructions below for if you did use --prefix=/usr

So, if you **DID** use --prefix=/usr then reinstalling all packages that begin with libglib2.0 with synaptic should solve the problem - I do not have an Ubuntu machine to hand so I cannot give you exact steps for this.

---

### Post by s1k3st on 2006-08-28
YOU ARE A GOD! Seriously though, thanks a lot:D

---

### Post by mdecler2 on 2006-08-28
I had a similar problem installing xchat...I hope this works.

---

### Post by rajamouli2000 on 2006-10-08
I used this to fix a similar prob that i had while installing Pygtk. thanks!

---

### Post by dfro on 2006-10-30
I was having similar errors trying to install atk so that I could install gtk+ so that I could install ardour.  
After reading this thread, I chose to uninstall glib, run ./configure --prefix=/usr on glib-2.12.0, and then make, make install it.  I then reinstalled all of the libglib2.0 files with synaptic. Now, when I try to run ./configure on atk, I am getting this error:

checking for GLIB - version >= 2.5.7... no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

I copied the /usr/lib/pkgconfig/glib2.0.pc file to /usr/local/lib/pkgconfig/glib2.0.pc, but I am getting the same error.

Any suggestions? Is it seeing the '1' in the 2.12.0 and thinking that is an earlier version than 2.5.7?

---

