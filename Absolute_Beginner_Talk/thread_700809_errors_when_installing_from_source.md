---
title: "errors when installing from source"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2008-02-18
Trying to install fragroute from source since the compiled version in synaptic does not want to work for me correctly. I am getting some errors when running checkinstall but do not see what the problem is. Any ideas?
Here is the result from sudo checkinstall:

[PHP]========================= Installation results ===========================
Making install in scripts
make[1]: Entering directory `/home/blake/security-applications/fragroute-1.2/scripts'
make[2]: Entering directory `/home/blake/security-applications/fragroute-1.2/scripts'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/blake/security-applications/fragroute-1.2/scripts'
make[1]: Leaving directory `/home/blake/security-applications/fragroute-1.2/scripts'
Making install in win32
make[1]: Entering directory `/home/blake/security-applications/fragroute-1.2/win32'
make[2]: Entering directory `/home/blake/security-applications/fragroute-1.2/win32'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/blake/security-applications/fragroute-1.2/win32'
make[1]: Leaving directory `/home/blake/security-applications/fragroute-1.2/win32'
make[1]: Entering directory `/home/blake/security-applications/fragroute-1.2'
gcc  -g -O2 -Wall  -o fragroute  fragroute.o argv.o bget.o mod.o pcaputil.o pkt.o randutil.o mod_delay.o mod_drop.o mod_dup.o mod_echo.o mod_ip_chaff.o mod_ip_frag.o mod_ip_opt.o mod_ip_ttl.o mod_ip_tos.o mod_order.o mod_print.o mod_tcp_chaff.o mod_tcp_opt.o mod_tcp_seg.o tun-loop.o strlcat.o strlcpy.o -L/usr/local/lib -ldnet -L/usr/local/lib -lpcap -L/usr/local/lib -levent 
fragroute.o: In function `fragroute_signal':
/home/blake/security-applications/fragroute-1.2/fragroute.c:151: undefined reference to `event_gotsig'
fragroute.o: In function `fragroute_init':
/home/blake/security-applications/fragroute-1.2/fragroute.c:181: undefined reference to `event_sigcb'
collect2: ld returned 1 exit status
make[1]: *** [fragroute] Error 1
make[1]: Leaving directory `/home/blake/security-applications/fragroute-1.2'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
[/PHP]

---

### Post by jan quark on 2008-02-18
well the compiling process is usually a three step
```

./configure
```

```
make
```

```
sudo make install
``` or
```
sudo check install
```

did you run it that way?

do you get any error messages when you do it that way ?

---

### Post by spiderbatdad on 2008-02-18
```
sudo apt-get install libevent1 libevent-dev 
```

---

