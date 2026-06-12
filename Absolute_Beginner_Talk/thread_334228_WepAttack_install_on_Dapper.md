---
title: "WepAttack install on Dapper"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by SimonNewbie on 2007-01-08
I am trying to install wepattack on Dapper and get this error.......

rooney@rooney-laptop:~/wep/WepAttack-0.1.3/src$ sudo make
Password:
gcc -fno-for-scope -c -D__LINUX_WLAN__ -D__I386__ -o wepfilter.o wepfilter.c
cc1: warning: command line option "-fno-for-scope" is valid for C++/ObjC++ but not for C
wepfilter.c:21:18: error: pcap.h: No such file or directory
wepfilter.c:117: warning: ‘struct pcap_pkthdr’ declared inside parameter list
wepfilter.c:117: warning: its scope is only this definition or declaration, which is probably not what you want
wepfilter.c: In function ‘my_callback’:
wepfilter.c:121: error: dereferencing pointer to incomplete type
wepfilter.c:127: error: dereferencing pointer to incomplete type
wepfilter.c:127: error: dereferencing pointer to incomplete type
wepfilter.c:129: error: dereferencing pointer to incomplete type
wepfilter.c:129: error: dereferencing pointer to incomplete type
wepfilter.c: In function ‘get_packets’:
wepfilter.c:236: error: ‘PCAP_ERRBUF_SIZE’ undeclared (first use in this function)
wepfilter.c:236: error: (Each undeclared identifier is reported only once
wepfilter.c:236: error: for each function it appears in.)
wepfilter.c:237: error: ‘pcap_t’ undeclared (first use in this function)
wepfilter.c:237: error: ‘descr’ undeclared (first use in this function)
wepfilter.c:239: error: storage size of ‘hdr’ isn’t known
make: *** [wepfilter.o] Error 1
rooney@rooney-laptop:~/wep/WepAttack-0.1.3/src$

I put the space in the Makefile after the log.o and before the back slash but i still get the error message.

This is the line in my Makefile.

wepattack:      wepattack.o rc4.o wepfilter.o log.o modes.o misc.o verify.o keygen.o
        $(LD) $(LDFLAGS) -o $@ wepattack.o rc4.o wepfilter.o log.o \
        modes.o misc.o verify.o keygen.o $(LIBS)


Thanks for any help,
Simon

---

