---
title: "Problems installing TOR"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2007-03-19
i have downloaded the latest version of TOR, installed libevent (made sure i had Zlib and OpenSSL) according to their webpage [http://tor.eff.org/docs/tor-doc-unix.html.en#privoxy](http://tor.eff.org/docs/tor-doc-unix.html.en#privoxy).  when i go to install tor according to the instructions this is what i get, at the end it says i have a config error with OpenSSL.

jqaskwig@poordamnedfool:~/Desktop/tor-0.1.1.26$ ./configure && make
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for library containing socket... none required
checking for library containing gethostbyname... none required
checking for library containing dlopen... -ldl
checking for library containing pthread_create... -lpthread
checking for library containing pthread_detach... none required
checking for libevent directory... (system)
checking whether we need extra options to link libevent... (none)
checking for OpenSSL directory... configure: error: Could not find a linkable OpenSSL. You can specify an explicit path using --with-ssl-dir

anyone know what im doing wrong?  thanks again

---

