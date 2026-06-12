---
title: "*simple* question - kernel source"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by Pumpernickel on 2005-06-27
While trying to install a driver, I ran into a problem - it requires the kernel sources.  Specifically, /usr/src/linux-2.6.10-5-386.  Unfortunately, nothing I can see in Synaptic seems to quite match that description, and although there are tons of references on the web to that directory, none of the ones I can see say where, specifically, I can get it.

This is particularly frustrating because I get the impression there's a ridiculously simple solution that I'm overlooking.

Any help?

---

### Post by word_virus on 2005-06-27
[QUOTE=Pumpernickel]While trying to install a driver, I ran into a problem - it requires the kernel sources.  Specifically, /usr/src/linux-2.6.10-5-386.  Unfortunately, nothing I can see in Synaptic seems to quite match that description, and although there are tons of references on the web to that directory, none of the ones I can see say where, specifically, I can get it.

This is particularly frustrating because I get the impression there's a ridiculously simple solution that I'm overlooking.

Any help?[/QUOTE]

Downloading the complete kernel source is usually overkill unless you want to compile your own kernel.  All you need are the kernel headers, which are available in Synaptic. Can't remember exactly what they're called... linux-headers-2.6.10-5-386 would probably be a good start, though.

After Synaptic downloads and installs that package, your driver should compile cleanly.

Hope this helps!

---

### Post by Pumpernickel on 2005-06-27
I have the kernel headers installed, but it's looking for that specific directory.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=Pumpernickel]While trying to install a driver, I ran into a problem - it requires the kernel sources.  Specifically, /usr/src/linux-2.6.10-5-386.  Unfortunately, nothing I can see in Synaptic seems to quite match that description, and although there are tons of references on the web to that directory, none of the ones I can see say where, specifically, I can get it.
[/QUOTE]

Hello. Well...you seem down on your skills...so I have a plan. I'll give you a howto with the answer and you have to dig it out (tell me if that rude, I'm trying to be fun):

[http://www.ubuntuforums.org/showthread.php?t=23596](http://www.ubuntuforums.org/showthread.php?t=23596)

Its easy when you see that.

---

### Post by Pumpernickel on 2005-06-27
Again, that should work - in theory - but it's looking for a specific directory.  I tried doing that earlier - even renaming the directory to match the one it expected to find the source code in - and got more errors as the install script choked on what it found that didn't match what it expected.


Enough people seem to say they have that directory (google search /usr/src/linux-2.6.10-5-386) that I'm sure that it a) is something specific and b) exists, but that doesn't seem to fit the bill.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=Pumpernickel]Again, that should work - in theory - but it's looking for a specific directory.  I tried doing that earlier - even renaming the directory to match the one it expected to find the source code in - and got more errors as the install script choked on what it found that didn't match what it expected.


Enough people seem to say they have that directory (google search /usr/src/linux-2.6.10-5-386) that I'm sure that it a) is something specific and b) exists, but that doesn't seem to fit the bill.[/QUOTE]

Do you have the headers installed? Sometimes weird stuff like that blocks you. You should try installing the 686 (or k7 if you have an new athon or the 686-smp if you have a system with hyperthreading). Then install that source and untar it and see if it works.

---

### Post by word_virus on 2005-06-27
[QUOTE=Pumpernickel]I have the kernel headers installed, but it's looking for that specific directory.[/QUOTE]

Ah, I see.  I didn't understand from your earlier post. Sorry! 

So, you are trying to install a driver that looks in a specific directory for the kernel sources and then fails when it can't find them, right? 

If you are installing this program from source there may be an option you can pass to configure to specifically tell it where to find the kernel headers, the first thing I would try is './configure --help' and see if you can find an option that looks appropriate.

Failing that, you could see if this is a variable defined in the Makefile, and then edit it there...

Unfortunately, I don't know off the top of my head in which directory Ubuntu keeps the kernel headers.... anybody?

---

### Post by az on 2005-06-27
Please do not keep secret the module you want to compile.


If it is properly created, the compile script will look in /lib/modules/(uname of running kernel)/build which is symlinked to your kernel headers or sources.

Installing the correct linux-headers package will create that symlink.

Other than that, you need to install linux-tree
untar the tarball in /usr/src
cd into it
copy the config from /boot
and compile the kernel so that you have the configured source.

---

