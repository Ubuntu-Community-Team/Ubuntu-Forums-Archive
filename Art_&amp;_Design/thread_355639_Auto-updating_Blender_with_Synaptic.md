---
title: "Auto-updating Blender with Synaptic?"
date: 2007-02-07
forum: Art &amp; Design
---

### Post by whitefort on 2007-02-07
Hi, Guys.

I've been reading the Ubuntu Hacks book, and learned how to configure Synaptic so that it gets the most recent releases of Wine - this was done by typing some kind of link to the Wine website into the advanced Synaptic configuration GUI - I typed it, but I didn't really understand it.

Anyway, it's important to me to always have an up-to-date Blender installation.  I was wondering if anyone could tell me the magic words to type into Symantic to link up to the Blender site and do the upgrades?

Thanks!

---

### Post by Nano Geek on 2007-02-08
Well, you can do them by hand using svn and scons.
If you want to do this copy this into the command line.```
sudo apt-get build-dep blender && sudo apt-get install cvs
cvs -z3 -d:pserver:anonymous@cvs.blender.org:/cvsroot/bf-blender co blender
cd ./blender
scons WITH_BF_OPENAL=0
```Hope this helps you.
It will probably take awhile so be patient.

---

### Post by whitefort on 2007-02-08
Hi, and thanks for the reply.

Unfortunately that didn't work, and I don't yet know enough about Linux to understand the error message:

~$ sudo apt-get build-dep blender && sudo apt-get install cvs
Password:
Reading package lists... Done
Building dependency tree... Done
Note, selecting freeglut3-dev instead of libglut-dev
Note, selecting libjpeg62-dev instead of libjpeg-dev
Package libpng-dev is a virtual package provided by:
  libpng12-dev 1.2.8rel-5ubuntu0.1
You should explicitly select one to install.
E: Package libpng-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for blender: libpng-dev

But thanks for trying to help!

---

### Post by Aldrik on 2007-02-08
[http://mediawiki.blender.org/index.php/BlenderDev/UbuntuBlenderCompile](http://mediawiki.blender.org/index.php/BlenderDev/UbuntuBlenderCompile)

---

### Post by whitefort on 2007-02-08
Thanks Aldrik.

I'm totally new to Linux, and I have to admit that trying to comple stuff from source still looks scary to me.

Can I take it that the short answer is, 'No, you can't use synaptic to get the latest version of Blender'?  ;)

---

### Post by Nano Geek on 2007-02-08
> **whitefort said:**
> Hi, and thanks for the reply.

Unfortunately that didn't work, and I don't yet know enough about Linux to understand the error message:

~$ sudo apt-get build-dep blender && sudo apt-get install cvs
Password:
Reading package lists... Done
Building dependency tree... Done
Note, selecting freeglut3-dev instead of libglut-dev
Note, selecting libjpeg62-dev instead of libjpeg-dev
Package libpng-dev is a virtual package provided by:
  libpng12-dev 1.2.8rel-5ubuntu0.1
You should explicitly select one to install.
E: Package libpng-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for blender: libpng-dev

But thanks for trying to help!Try this instead:```
sudo apt-get install libpng12-dev
```

---

### Post by whitefort on 2007-02-08
> **asjdfwejqrfjcvm msz34rq33 said:**
> Try this instead:```
sudo apt-get install libpng12-dev
```

Thanks again.  I tried that, then the first commands you gave me.  All sorts of downloading and compiling stuff happened, for quite a long time - but at the end of it I had a message that building stopped because of errors.

Thankfully my old Blender is still OK, but still no new one.  :( 

But thanks for trying to help - I really appreciate it.

---

### Post by Nano Geek on 2007-02-08
If you want you can post your error message and I can take a look at it.

---

