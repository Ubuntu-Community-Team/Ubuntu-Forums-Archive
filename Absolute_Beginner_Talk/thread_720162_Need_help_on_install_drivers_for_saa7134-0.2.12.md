---
title: "Need help on install drivers for saa7134-0.2.12"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Lennrev on 2008-03-10
I am new to Linux. I have this video capture card i have been trying to get work with ubuntu studio. After downloading the drivers and i tried to make them this is what i got:

root@reen:/home/vernel/saa7134-0.2.12# make
make -C /lib/modules/2.6.24-11-rt/build SUBDIRS=/home/vernel/saa7134-0.2.12 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-11-generic'
  CC [M]  /home/vernel/saa7134-0.2.12/video-buf.o
/home/vernel/saa7134-0.2.12/video-buf.c:46: error: expected ')' before string constant
/home/vernel/saa7134-0.2.12/video-buf.c: In function 'videobuf_vmalloc_to_sg':
/home/vernel/saa7134-0.2.12/video-buf.c:68: error: 'struct scatterlist' has no member named 'page'
/home/vernel/saa7134-0.2.12/video-buf.c: In function 'videobuf_pages_to_sg':
/home/vernel/saa7134-0.2.12/video-buf.c:96: error: 'struct scatterlist' has no member named 'page'
/home/vernel/saa7134-0.2.12/video-buf.c:104: error: 'struct scatterlist' has no member named 'page'
make[2]: *** [/home/vernel/saa7134-0.2.12/video-buf.o] Error 1
make[1]: *** [_module_/home/vernel/saa7134-0.2.12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-11-generic'
make: *** [default] Error 2

What should i do to correct this?

---

### Post by tzulberti on 2008-03-10
Why are you compiling the sources. Ubuntu already includes them in its kernell. For making the tv video capture, you should create a file called saa7134 in /etc/modrpobe.d/, but the contents of the file depends on you country.

Even if this is for Gentoo, it should guide you in Ubuntu. 
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

---

### Post by Lennrev on 2008-03-11
:) Gracias por su ayudar.

---

