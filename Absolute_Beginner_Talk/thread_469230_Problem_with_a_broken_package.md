---
title: "Problem with a broken package"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by ahoman66 on 2007-06-09
I have just updated my system. I use Ubuntu 7.04 and I have a broken package.
Here is the error I recieve...

E: /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a

I have tried to use fix broken packages in Synaptic no help.

I tried to remove libmjpegtools0c2a first before installing libmjpegtools0 uable to get the error above. Any help would be great.

Thank you
Allen

---

### Post by diatribe on 2007-06-09
try typing
sudo apt-get -f upgrade

---

### Post by ahoman66 on 2007-06-09
I tried that and this is the error message I recieved...

Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks 
Allen

---

### Post by media_555 on 2008-03-02
Any Gurus around, pls help! I am also getting the same error with Hardy (my trial), but with Open Office related package.. 

Can not update or install any other packages because of it. :(

---

### Post by Detox06 on 2008-06-07
Having the same problem. When I try to run updatemanager I get: E: /var/cache/apt/archives/libmjpegtools0_1.8.0-0.2_i386.deb: trying to overwrite `/usr/lib/liblavfile-1.8.so.0.0.0', which is also in package libmjpegtools0c2a. 

apt-get autoremove, apt-get install -f don't work, neither does broken packages in synaptic.

---

### Post by scrooge_74 on 2008-06-07
sudo dpkg -r --force- name of package

or sudo dpkg -P package

play around with dpkg until you get it right

---

