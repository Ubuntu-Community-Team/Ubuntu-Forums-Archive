---
title: "Airpwn Headers?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Airpwn requires some headers, does anyone know what they are?

---

### Post by joshrobinson on 2008-04-05
kernel headers maybe?

is it giving you an error on compiling or something?

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Yeah, I'm trying to compile it, but it needs some headers. Which would it be?

---

### Post by joshrobinson on 2008-04-05
can you post the error?

and whats airpwn anyway

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Packet injection tool, using it for security testing.

configure: error: required header missing..

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
@jd-laptop:~/Desktop/Other/airpwn-1.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for libnet_build_tcp in -lnet... yes
checking for pcap_open_live in -lpcap... yes
checking for pcre_compile in -lpcre... yes
checking for pthread_create in -lpthread... yes
checking for tx80211_txpacket in -lorcon... yes
checking for MD5_Init in -lssl... no
configure: openssl required for full WEP key generation
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... no
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for unistd.h... (cached) yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking libnet.h usability... yes
checking libnet.h presence... yes
checking for libnet.h... yes
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking tx80211.h usability... yes
checking tx80211.h presence... yes
checking for tx80211.h... yes
checking tx80211_packet.h usability... yes
checking tx80211_packet.h presence... yes
checking for tx80211_packet.h... yes
checking openssl/md5.h usability... no
checking openssl/md5.h presence... no
checking for openssl/md5.h... no
configure: error: required header missing..


that's everything that comes up when i do ./configure

---

### Post by JoshuaRL on 2008-04-05
Its a wireless client penetration tool.

And yes, please post the output you are getting from the terminal.

---

### Post by joshrobinson on 2008-04-05
try

```
sudo apt-get install libssl-dev
```

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Let me try it.

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Excellent.

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Now IFNAMSIZ is undeclared.

---

### Post by joshrobinson on 2008-04-05
post the error

---

### Post by mc4man on 2008-04-05
> and whats airpwn anyway
it's a little kiddie hacking, spoofing tool, on juvenile delinquent level

---

