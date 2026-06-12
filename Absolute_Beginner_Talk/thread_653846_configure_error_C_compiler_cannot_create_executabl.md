---
title: "configure: error: C compiler cannot create executables"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by latheesan on 2007-12-30
Hello,

On my machine, i used **apt-get install build-essential** to get the packages needed so i can compile apps.

It seems the installer apt-get installed the latest version of GCC on my machine (gcc-4.1). This is a big problem because, when i type the ./configure i get the following error:

> configure: error: C compiler cannot create executables

So i told a friend of mine about this who was good with linux and what he did was downgraded my GCC to version 3.3 and i was able to successfully compile and the app i compiled worked 100% without a problem.

When i tried to compile another app, gcc-3.3 was not compatible, so i had to use apt-get upgrade to get the new version of gcc. Now, i want to go back to gcc-3.3 however my friend is not here to help.

How do i uninstall any version of GCC and install gcc-3.3 and make that the default GCC version, nothing else?

---

### Post by markharding557 on 2007-12-30
you can install install gcc-3.3 from synaptic,iv'e tested this and synaptic does not uninstall the other version during installation so can have both installed at the same time.
having said that you can remove gcc-4.1 in synaptic if you wish
in case you are not sure synaptic is a front for apt and does the same thing

---

### Post by latheesan on 2007-12-30
thanks for that, i got rid of gcc-4.1 using apt-get remove <package name> and then installed the version i wanted then i used **export CC=gcc-3.3** to make my compiler use the specific version during compilation..

Now that i got the  GCC sorted, i tried to compile my app using the following commands (as instructed):

[B]./configure
make clean
make sql[/B]

As soon as i did that, i got the following error :

> MySQL not found or disabled by the configure script

The wierd thing is, i DO have MySQL installed and it's working fine... This is the **config.log** created when i issued my ./configure command : 

[http://pastebin.ca/839010](http://pastebin.ca/839010)

Does anyone know what package i might be missing? I can't compile this app that uses mysql library for some reason :(

---

### Post by latheesan on 2007-12-30
Any idea? please advice.

---

### Post by ^rooker on 2007-12-30
I guess it is asking for the mysql-source to be installed. 
Try to install the mysql-source package.

---

