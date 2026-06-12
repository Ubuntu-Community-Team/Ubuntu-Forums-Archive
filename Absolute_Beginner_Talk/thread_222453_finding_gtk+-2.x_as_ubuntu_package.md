---
title: "finding gtk+-2.x as ubuntu package"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Micik on 2006-07-25
Hello,
can anyone suggest me link where I can find newer version of gtk+2.x? I have downloaded source in tar.gz, but I have dependencies problem installing it. I think if I find .deb I'll have less problem.
I looked under archive.ubuntu.com, but there are tar.gz and also some .deb files. Please can you suggest link for download gtk as deb package, because I think I'll have less headache installing it.

---

### Post by simonn on 2006-07-25
What are you actually trying to do?

You probably do not need a newer version of GTK.

---

### Post by Micik on 2006-07-25
when trying to install anjuta 2.0.2 I get error message that dependency gtk is not satidfied. That's why I need to instal gtk+.
Is there any way I can check if gtk+ is installed and what version is installed?

---

### Post by simonn on 2006-07-25
If you are running gnome you already have it installed, but not the dev package.

Install libgtk2.0-dev (using synaptic, apt-get or whatever).

If not post the actual error you get.

I would be very suprised if Anjuta 2 required a later version of GTK.

---

### Post by Micik on 2006-07-26
Here's what error mesage I get when trying to install anjuta from source(./configure command)

...
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for GOBJECT... yes
checking for GMODULE... yes
checking for GTHREAD... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.8.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Is there any way to check whether gtk+ is installed and which version?
What else could cause such error?

Thanks

---

### Post by Perfect Storm on 2006-07-26
On dapper it's 2.8.18 so the only thing you need is to install the -dev package for compiling, if you use a previous version of Ubuntu you might run into trouble.

```
sudo apt-get install libgtk2.0-dev
```

---

### Post by RichC on 2006-08-25
I have a similar problem trying to ./configure a GTK program and get the following error message:

checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I have libgtk1.2-dev installed, and I am running BREEZY.

I noticed the last answer here said versions of Ubuntu previous to DAPPER might have trouble. Can I not overcome this problem in BREEZY?

Thanks

---

### Post by RichC on 2006-08-26
I discovered another GTK related package in one of the repositories:

libgtk+2.0-directfb.udeb-dev  2.0.9-5

After I installed it, ./configure runs OK on my GTK program without the error message mentioned in my last post. :)

---

