---
title: "Help with installation of new apps"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Aenigma on 2006-10-05
Ok so after installing Ubuntu for my second time, and finaly getting my Sagem Fast 800 modem working and getting online with linux ive come to anbother problem. Now this will sound stupid, but i need to get it sorted.
When installing, well attempting to install new apps i follow the readme through the step
./configure
i then type "make"
and get this:
"make: *** No targets specified and no makefile found.  Stop."
I cant figure out why, could someone please help me.

---

### Post by xyz on 2006-10-05
Hi,
Try this it's a good start:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Psquared on 2006-10-05
> **Aenigma said:**
> Ok so after installing Ubuntu for my second time, and finaly getting my Sagem Fast 800 modem working and getting online with linux ive come to anbother problem. Now this will sound stupid, but i need to get it sorted.
When installing, well attempting to install new apps i follow the readme through the step
./configure
i then type "make"
and get this:
"make: *** No targets specified and no makefile found.  Stop."
I cant figure out why, could someone please help me.

You probably don't have "make" and the associated packages installed. Go to synaptic, or use apt-get, and install the "build-essentials" package. That should install make and make install which you need after ./configure.

If that is not it you may just have a bad download or some unmet dependency. Do you see any other errors in the terminal screen.?

---

### Post by Dinerty on 2006-10-05
Do you have build-essential installed?

```
sudo apt-get install build-essential
```

Next always check "readme" files in the directory, as it will give specific instructions to that package.

If there are none there, then check forums for advice

---

### Post by Aenigma on 2006-10-05
I have the Build essentials, as i needed them to install the drivers for my modem, and these drivers installed fine. iv just read the How To Install ANYTHING guide and i havnt learnt anything new from that really.

I just ran ./config again to get the code and for the first time i got this error.


checking for GLIB - version >= 2.0.3... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: "Cannot find glib"

---

### Post by Dinerty on 2006-10-05
> **Aenigma said:**
> I have the Build essentials, as i needed them to install the drivers for my modem, and these drivers installed fine. iv just read the How To Install ANYTHING guide and i havnt learnt anything new from that really.

I just ran ./config again to get the code and for the first time i got this error.


checking for GLIB - version >= 2.0.3... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: "Cannot find glib"

I think you may need to install libgtk2.0-dev

---

