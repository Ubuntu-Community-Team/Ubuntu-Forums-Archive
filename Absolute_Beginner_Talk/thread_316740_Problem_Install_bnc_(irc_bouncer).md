---
title: "Problem Install bnc (irc bouncer)"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Najib on 2006-12-11
Hi. im just new to ubuntu. i got problem with "make" when trying to install bnc

./configure ( OK )
.make ( failed )

***make error logs *****


root@najib:~/test/bnc2.8.6# make
gcc -O3 -Wall -c bnc.c
In file included from bnc.c:18:
sbuf.h:38:64: warning: no newline at end of file
gcc -O3 -Wall -c conf.c
In file included from conf.c:9:
sbuf.h:38:64: warning: no newline at end of file
conf.c: In function ‘loadconf’:
conf.c:371: warning: pointer targets in passing argument 1 of ‘fgets’ differ in signedness
conf.c:377: warning: pointer targets in passing argument 1 of ‘strtok’ differ in signedness
gcc -O3 -Wall -c server.c
In file included from server.c:21:
sbuf.h:38:64: warning: no newline at end of file
server.c: In function ‘xsockprint’:
server.c:136: warning: pointer targets in passing argument 1 of ‘vsnprintf’ differ in signedness
server.c: In function ‘logprint’:
server.c:148: warning: pointer targets in passing argument 1 of ‘vsnprintf’ differ in signedness
server.c:150: warning: pointer targets in passing argument 2 of ‘bnclog’ differ in signedness
server.c: In function ‘send_queued’:
server.c:374: warning: pointer targets in passing argument 2 of ‘sbuf_pagemap’ differ in signedness
server.c: In function ‘identwd_unlock’:
server.c:526: warning: pointer targets in passing argument 3 of ‘getsockname’ differ in signedness
server.c: In function ‘addon_client’:
server.c:972: warning: pointer targets in passing argument 3 of ‘getpeername’ differ in signedness
server.c: In function ‘ircproxy’:
server.c:1087: warning: pointer targets in passing argument 3 of ‘accept’ differ in signedness
gcc -O3 -Wall -c cmds.c
In file included from cmds.c:12:
sbuf.h:38:64: warning: no newline at end of file
cmds.c: In function ‘handlepclient’:
cmds.c:470: warning: pointer targets in passing argument 1 of ‘fgets’ differ in signedness
cmds.c:472: warning: pointer targets in passing argument 1 of ‘remnl’ differ in signedness
cmds.c:508: error: label at end of compound statement
cmds.c: In function ‘cmd_vip’:
cmds.c:1071: error: label at end of compound statement
make: *** [cmds.o] Error 1
root@najib:~/test/bnc2.8.6# ](*,) :evil:

---

### Post by Najib on 2006-12-12
bump...anyone got idea?

---

### Post by deadgobby on 2006-12-12
What are you trying to install from Source? Did you check into Synaptic before installing from source?
Gobby

---

### Post by Najib on 2006-12-20
just solve my problem. forget to install tcl/tck libs :p

---

