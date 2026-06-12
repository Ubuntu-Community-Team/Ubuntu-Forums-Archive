---
title: "Trouble compiling Hydra"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by I_R_LEENUCKS_MAN on 2008-04-04
I can do the ./configure ok, but when I get to make install it says:

root@jd-laptop:/home/jd/Desktop/Other/hydra-0.1.8# make install
Making install in contrib
make[1]: Entering directory `/home/jd/Desktop/Other/hydra-0.1.8/contrib'
Making install in redhat
make[2]: Entering directory `/home/jd/Desktop/Other/hydra-0.1.8/contrib/redhat'
make[3]: Entering directory `/home/jd/Desktop/Other/hydra-0.1.8/contrib/redhat'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jd/Desktop/Other/hydra-0.1.8/contrib/redhat'
make[2]: Leaving directory `/home/jd/Desktop/Other/hydra-0.1.8/contrib/redhat'
make[2]: Entering directory `/home/jd/Desktop/Other/hydra-0.1.8/contrib'
make[3]: Entering directory `/home/jd/Desktop/Other/hydra-0.1.8/contrib'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jd/Desktop/Other/hydra-0.1.8/contrib'
make[2]: Leaving directory `/home/jd/Desktop/Other/hydra-0.1.8/contrib'
make[1]: Leaving directory `/home/jd/Desktop/Other/hydra-0.1.8/contrib'
Making install in examples
make[1]: Entering directory `/home/jd/Desktop/Other/hydra-0.1.8/examples'
make[2]: Entering directory `/home/jd/Desktop/Other/hydra-0.1.8/examples'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jd/Desktop/Other/hydra-0.1.8/examples'
make[1]: Leaving directory `/home/jd/Desktop/Other/hydra-0.1.8/examples'
Making install in src
make[1]: Entering directory `/home/jd/Desktop/Other/hydra-0.1.8/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../    -g -O2 -pthread -pipe -Wall -MT cgi_ssl.o -MD -MP -MF ".deps/cgi_ssl.Tpo" -c -o cgi_ssl.o cgi_ssl.c; \
        then mv -f ".deps/cgi_ssl.Tpo" ".deps/cgi_ssl.Po"; else rm -f ".deps/cgi_ssl.Tpo"; exit 1; fi
cgi_ssl.c:22:25: error: gnutls/x509.h: No such file or directory
make[1]: *** [cgi_ssl.o] Error 1
make[1]: Leaving directory `/home/jd/Desktop/Other/hydra-0.1.8/src'
make: *** [install-recursive] Error 1


I'm using su privileges...

Help!

---

### Post by I_R_LEENUCKS_MAN on 2008-04-04
I'm using this for wireless security testing on a corporate network, by the way, so that you guys don't think I'm some hacker or something.

---

### Post by I_R_LEENUCKS_MAN on 2008-04-04
Anyone help...?

---

### Post by mc4man on 2008-04-05
Did you run make first ?
edit ;here's little snippet - look familiar ?```
[CODE]
doug@doug-desktop:~/Desktop/hydra-0.1.8$ make
make  all-recursive
make[1]: Entering directory `/home/doug/Desktop/hydra-0.1.8'
Making all in contrib
make[2]: Entering directory `/home/doug/Desktop/hydra-0.1.8/contrib'
Making all in redhat
make[3]: Entering directory `/home/doug/Desktop/hydra-0.1.8/contrib/redhat'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/doug/Desktop/hydra-0.1.8/contrib/redhat'
make[3]: Entering directory `/home/doug/Desktop/hydra-0.1.8/contrib'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/doug/Desktop/hydra-0.1.8/contrib'
make[2]: Leaving directory `/home/doug/Desktop/hydra-0.1.8/contrib'
Making all in examples
make[2]: Entering directory `/home/doug/Desktop/hydra-0.1.8/examples'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/hydra-0.1.8/examples'
Making all in src
make[2]: Entering directory `/home/doug/Desktop/hydra-0.1.8/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../    -g -O2 -pthread -pipe -Wall -MT alias.o -MD -MP -MF ".deps/alias.Tpo" -c -o alias.o alias.c; \
        then mv -f ".deps/alias.Tpo" ".deps/alias.Po"; else rm -f ".deps/alias.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../    -g -O2 -pthread -pipe -Wall -MT boa.o -MD -MP -MF ".deps/boa.Tpo" -c -o boa.o boa.c; \
        then mv -f ".deps/boa.Tpo" ".deps/boa.Po"; else rm -f ".deps/boa.Tpo"; exit 1; fi
boa.c: In function ‘create_server_socket’:   ..............................
 
```[/CODE]

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Never mind, fixed.

Thanks for the help anyways.

---

### Post by joshrobinson on 2008-04-05
i know you figured out your problem already, but this is a neat way of figuring out what dev package you need to compile specific source code

```
sudo apt-get install apt-file
```
```
sudo apt-file update
```

```
f gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../ -g -O2 -pthread -pipe -Wall -MT cgi_ssl.o -MD -MP -MF ".deps/cgi_ssl.Tpo" -c -o cgi_ssl.o cgi_ssl.c; \
then mv -f ".deps/cgi_ssl.Tpo" ".deps/cgi_ssl.Po"; else rm -f ".deps/cgi_ssl.Tpo"; exit 1; fi
cgi_ssl.c:22:25: error: gnutls/[COLOR="Red"]x509.h[/COLOR]: No such file or directory
make[1]: *** [cgi_ssl.o] Error 1
make[1]: Leaving directory `/home/jd/Desktop/Other/hydra-0.1.8/src'
make: *** [install-recursive] Error 1
```

so run this
```
sudo apt-file search x509.h
```

```

libgnutls-dev: /usr/include/gnutls/x509.h

```
```
sudo apt-get install libgnutls-dev
```

and there you go :)

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Awesome!

I'll put that in a gEdit or something so that I can reference it. Thanks!

By the by, do you know which libnet airpwn1.3 requires?

---

### Post by joshrobinson on 2008-04-05
probably libnet1-dev

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Well, I'll try out your trick.

---

