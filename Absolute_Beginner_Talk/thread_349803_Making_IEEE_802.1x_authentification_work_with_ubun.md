---
title: "Making IEEE 802.1x authentification work with ubuntu"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by KeyOh on 2007-01-30
I am a complete newb with linux in general. But I'm trying to enable my internet connection with linux. Unfortunately my university broadband requires 802.1x authentification. I've read a couple of guides on how to do it, and it seems like I need two programs: OpenSSL and xSupplicant. I've managed to download the two programs through Windows, and moved them over to Ubuntu. The two files I've downloaded is: openssl-0.9.8d.tar.gz and xsupplicant-1.2.8.tar.gz

The question is how do I install and use these two programs?

I would be very greatful for any help, thank you for taking care of the linux newbs in the world =)

---

### Post by mikewhatever on 2007-01-30
Try this page [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
It looks like the 4-th option is relevant.

---

### Post by KeyOh on 2007-01-31
Thanks, I've now tried that and it worked smoothly (I think) with openssl. However I ran into some problems with xsupplicant. When I typed: sudo ./configure

this happened:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... yes
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for ranlib... ranlib
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

When I try to run: sudo make
make: *** No targets specified and no makefile found.  Stop.


Is it my tar.gz file wich is the problem? I downloaded it from: [http://sourceforge.net/project/showfiles.php?group_id=60236](http://sourceforge.net/project/showfiles.php?group_id=60236)

How do I check if my openssl installation worked ok?

---

