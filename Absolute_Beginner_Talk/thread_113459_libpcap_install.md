---
title: "libpcap install?"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by spikes2020 on 2006-01-06
installing weplab had been a pain in the a$$, it keeps asking for libpcap-dev and i have tryed to install it for the past hour and a half, so far i downloaded libpcap-0.7.2 from [here]("http://packages.debian.org/unstable/libdevel/libpcap0.7-dev") and i get no where.



and i extracted it and did 

./configure

that seemed to work ok it needed flux and some other things but i just used (sudo apt-get install <stuff>) then it finaly did not give me any errors, then i did 

make

{{
spikes@spikes:~/Ubuntu/libpcap-0.7.2$ make
bison -y -p pcap_ -d grammar.y
mv y.tab.c grammar.c
mv y.tab.h tokdefs.h
gcc -O2 -I.  -DHAVE_CONFIG_H -c scanner.c
gcc -O2 -I.  -DHAVE_CONFIG_H -Dyylval=pcap_lval -c grammar.c
sed -e 's/.*/char pcap_version[] = "&";/' ./VERSION > version.c
gcc -O2 -I.  -DHAVE_CONFIG_H -c version.c
ar rc libpcap.a pcap-linux.o pcap.o inet.o gencode.o optimize.o nametoaddr.o etherent.o savefile.o bpf_filter.o bpf_image.o bpf_dump.o scanner.o grammar.o version.o
ranlib libpcap.a
}}

and this is where i get lost, i dont know where to go from this?



thanx

spikes2020

---

### Post by spikes2020 on 2006-01-06
ok i got libpcap-dev installed, i had to add some new funky thing to my sources.list and then just used apt-get. 

but im still getting a problem on installing weplab

i got the (./configure) to work and it made a make file than i need to just run (make) and then (make install) but it gets an error as shown


{{

spikes@spikes:~/Ubuntu/weplab-0.1.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c

(did some stuff)

warning: compiler is not known: not optimizing!
using gcc -g -O2 -Wall -pipe
configure: creating ./config.status
config.status: creating Makefile

spikes@spikes:~/Ubuntu/weplab-0.1.5$ make
gcc  -g -O2 -Wall -pipe  -o weplab  main.o analpfile.o bruteforce.o capture.o debug.o dictionary.o globals.o heuristics.o md5.o wep.o attack.o  -lpcap
capture.o: In function `captureWeakPackets':
/home/spikes/Ubuntu/weplab-0.1.5/capture.c:171: undefined reference to `pcap_dump_flush'
collect2: ld returned 1 exit status
make: *** [weplab] Error 1
spikes@spikes:~/Ubuntu/weplab-0.1.5$


}}

---

