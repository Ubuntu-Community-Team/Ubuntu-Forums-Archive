---
title: "Error in Installation of TinyOS-2.x"
date: 2014-12-25
forum: Any Other OS
---

### Post by mehak2 on 2014-12-25
Hi,
actually I face error in TinyOS configuration. I set the path of python package in sim.extra, python 2.7 package is used. In sim.extra, I changed the $PYTHONVERSION variable and include the CFLAG = -I/path. After these changing, error (python2.5 is not found) was solved. But following error comes when I type "make telosb sim": 

user@XubunTOS:~/Desktop/tinyos-2.x/apps/Blink$ make telosb sim
mkdir -p simbuild/telosb
  placing object files in simbuild/telosb
  writing XML schema to app.xml
  compiling BlinkAppC to object file sim.o
ncc -c -shared -fPIC -o simbuild/telosb/sim.o -g -O0 -tossim -fnesc-nido-tosnodes=1000 -fnesc-simulate -fnesc-nido-motenumber=sim_node\(\) -fnesc-gcc=gcc -Wall -Wshadow -Wnesc-all -target=telosb -fnesc-cfile=simbuild/telosb/app.c -board= -DDEFINED_TOS_AM_GROUP=0x22 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"user\" -DIDENT_HOSTNAME=\"XubunTOS\" -DIDENT_USERHASH=0x184e7486L -DIDENT_TIMESTAMP=0x549be41eL -DIDENT_UIDHASH=0x16166ad0L -Wno-nesc-data-race BlinkAppC.nc   -fnesc-dump=components -fnesc-dump=variables -fnesc-dump=constants -fnesc-dump=typedefs -fnesc-dump=interfacedefs -fnesc-dump=tags -fnesc-dumpfile=app.xml
Unknown target telosb
Known targets for TinyOS directory /home/user/top/t2_cur/tinyos-2.x/tos
and the specified include directories are:
  mulle z1 micaz tinynode gnode shimmer2 sam3s_ek intelmote2 iris surf mm5s epic ucmini span eyesIFXv2 eyesIFXv1 moteist5 telosa mica2dot mica2 sam3u_ek telosb shimmer shimmer2r btnode3 null red
make: *** [sim-exe] Error 2


I don't understand this error. Actually these all platfroms are already exist in tinyos folder.

Please help me. Its urgent. 
Thanks in advance

---

### Post by oldos2er on 2014-12-25
Moved to Other OS Support and Projects. If you need urgent help the best place to get it would be the tinyos-help mailing list; see [http://www.tinyos.net/community.html](http://www.tinyos.net/community.html)

---

