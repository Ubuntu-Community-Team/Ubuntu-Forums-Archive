---
title: "Libs?"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-01-12
I've come across this a few times...

When installing a package, say I get an error message saying that a certain lib ( in this exact case Glib ) is missing, how would I go about getting it, generally? ( I say generally, because I might need to apply this knowledge to another lib at a later date )

Thanks

---

### Post by kairu0 on 2006-01-12
One easy way is to look at the name of the lib, and then search for a package with a similar name on packages.ubuntu.com. For example, if it says you are missing libxosd, you could search for "xosd."

You can also do pretty much the same thing in Synaptic, but packages.ubuntu.com also let's you search for individual files, so it's more convenient sometimes.

---

### Post by Jimmey on 2006-01-12
What should I look for in the case of glib?

---

### Post by kairu0 on 2006-01-13
[QUOTE=Jimmey]What should I look for in the case of glib?[/QUOTE]

Are you trying to install a non-Ubuntu Debian package?

Glib is one of those essential, core packages whose presence is kind of taken for granted.

---

### Post by AMD64_N_Linux on 2006-01-13
Open Sympatic, and do a name search for " glib ". This will save you time by not having to look thru all of the files that have glib in the " description " ( a bunch ).

As far as I know, all of the libraries start with lib, in this case " libglib ".

Then you have different versions of the glib. 

2 hints. 

1. AFAIK, installing libraries you DONT need never hurts anything, unless they conflict with others. It will take some hdd space, but no biggie.

2. You may save some time by, when you first open sympatic, look in the left hand pane, at the bottom, click on Custom. Then click on BROKEN at the top.

If you have programs installed that are missing libraries, they will "usually " be listed there. It is a good idea to check the broken section every now and again anyway.

Hope this helped. And there maybe someone here more knowlegable about apt-get command line to help you that way, but if you have X Windows running, that is the way I would go.

---

### Post by benplaut on 2006-01-13
what program were you trying to install? if it's a bug, should be reported to the MOTU

---

### Post by Jimmey on 2006-01-13
AVI plugin for XMMS

---

### Post by Jimmey on 2006-01-13
It says, in the package manager, that 
'libglib' is installed, but when I try 
```
./configure
```
for the XMMS plugin, it says I haven't.
It says
> configure: error: *** GLIB >= 1.2.2 not installed - please install first ***


Any ideas?

---

### Post by AMD64_N_Linux on 2006-01-13
I have a couple of different versions of the " libglib " installed here on  breezy. 
 
 Do you have the right version already installed ?
 
 You said " ./configure " are you trying to compile the source code ? If so, you may need the libglib-development package to compile the XMMS plugin.

---

### Post by Jimmey on 2006-01-13
Ahh, that might be it. 
Thanks.
Edit:
It worked, but is now saying
> configure: error: *** GTK+ >= 1.2.2 not installed - please install first ***

What do I have to get there? It's slightly confusing, because for Glib, I had to get libglib-dev;
So what to I get to sort that out?

---

### Post by public_void on 2006-01-13
> ... It's slightly confusing, because for Glib, I had to get libglib-dev;
When I've complied from source I've noticed that, why is that?

---

### Post by Jimmey on 2006-01-13
So, what GTK should I get? And from where?

---

### Post by AMD64_N_Linux on 2006-01-13
[quote=Jimmey]So, what GTK should I get? And from where?[/quote]

You should look at the README file in the directory of the plugin source code. It should have a version number of the all of the "various" libraries you may need. 

gtk-dev might fix it, or it might need 7 or 8 or more dev-libs.

real quick, the difference between a libgtk and the libgtk-dev, is that the libgtk is for a precompiled binary file, linked to that library.

Now the libgtk-dev, or any-dev for that matter, is when you are compiling the binary yourself.

I hope that was clear enough.

---

### Post by Gustav on 2006-01-13
Almost always when you compile stuff there are libraries that that program needs. Then you need to install the development version of that library (mostly named lib<name of the library>-dev) which contains header files and such.

---

