---
title: "How to install GCC on Ubuntu 7.04 installeted from a live cd ??"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by bambubambu2 on 2007-10-04
ok this is my  problem:
i have no internet , none ,only the live cd .

i  installed the live cd on my computer and with synapse manager i installed something like g++ and build essential from the  live cd + sinoptic manager

the problem : i can't install  the multimedia codec becouse seems theat the compiler gcc don't fid something (i don't remember what exactley)

question : what should i do for having the complete gcc compiler ?i found it on the internet (has 45 mb)

ok  now what should i do to install the compiler ? must burn the gcc on a cd and use the synoptic on it ?

afterwards must use necesarly the line sudo get-install build essential , or the synoptic does everything?

any ideea to get myself a gcc compiler on my machine?



thx

---

### Post by Jussi Kukkonen on 2007-10-04
> any ideea to get myself a gcc compiler on my machine?
If you installed build-essential, you already have gcc. You are missing something else. Maybe you should start with explaining what you want to accomplish, how you tried to do it and what error messages you are getting.

---

### Post by bambubambu2 on 2007-10-04
ok this is what i tried to install :


gst-plugins-ugly-0.10.6  and

gst-plugins-bad 0-10.5


./cofigure

the last line :

Checking for GLID...configure:error:this packege riequire GLib=2.6 to compile


ANY IDEEA ?what should i do ?

---

### Post by Fixman on 2007-10-04
Simple:

```
sudo apt-get install build-essential
```

---

### Post by bambubambu2 on 2007-10-04
done


the same error.


Any ideea ??

---

### Post by bambubambu2 on 2007-10-04
help.
situation critical

---

### Post by Paul820 on 2007-10-04
> sudo apt-get install libglib2.0-dev

It is looking for the development headers.

---

### Post by Steveway on 2007-10-04
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
You should first setup a connection to the internet, you won't be satisfied on Ubuntu without Net.

---

### Post by stchman on 2007-10-04
> **bambubambu2 said:**
> ok this is my  problem:
i have no internet , none ,only the live cd .

i  installed the live cd on my computer and with synapse manager i installed something like g++ and build essential from the  live cd + sinoptic manager

the problem : i can't install  the multimedia codec becouse seems theat the compiler gcc don't fid something (i don't remember what exactley)

question : what should i do for having the complete gcc compiler ?i found it on the internet (has 45 mb)

ok  now what should i do to install the compiler ? must burn the gcc on a cd and use the synoptic on it ?

afterwards must use necesarly the line sudo get-install build essential , or the synoptic does everything?

any ideea to get myself a gcc compiler on my machine?



thx

gcc is installed by default on Ubuntu.  You will need build-essential for all the libraries.

---

