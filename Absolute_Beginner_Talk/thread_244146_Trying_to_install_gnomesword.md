---
title: "Trying to install gnomesword"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by eg-maverick on 2006-08-26
Hi.
I'm trying to install gnomesword (on ubuntu 6.06). I downloaded the tar file and extracted it to /tmp. Then I read README and INSTALL which tell me to execute configure and then make. I tried. I entered code:
sudo ./configure
It seems to have run to completion satisfactorily. Then I entered code:
sudo make
This is what I get:
name@ubuntu:/tmp/gnomesword-2.1.7$ sudo ./configure
Password:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... name@ubuntu:/tmp/gnomesword-2.1.7$ sudo make
make: *** No targets specified and no makefile found.  Stop.
name@ubuntu:/tmp/gnomesword-2.1.7$ make
make: *** No targets specified and no makefile found.  Stop.
name@ubuntu:/tmp/gnomesword-2.1.7$ sudo make install
make: *** No rule to make target `install'.  Stop.

I don't know what to do next?
Thanks.
Craig

---

### Post by aysiu on 2006-08-26
Try going to System > Administration > Synaptic Package Manager > Settings > Repositories. Check all the boxes.

Then click Reload. Search for *gnomesword* and mark it for installation. Then click Apply.

For more info, go here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

