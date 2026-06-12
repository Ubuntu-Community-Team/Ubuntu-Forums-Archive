---
title: "libpcap"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by lfvo on 2006-01-17
hi
i am new on linux, and i am try to open this aplication and give me this error

> root@sala:/home/luis/Programas/netcount# ./Netcount
./Netcount: error while loading shared libraries: libpcap.so.0: cannot open shared object file: No such file or directory

can anyone help me

---

### Post by ape on 2006-01-17
You need to install the libpcap0.8 package (and possibly the libpcap0.8-dev if required).

---

### Post by lfvo on 2006-01-17
[QUOTE=ape]You need to install the libpcap0.8 package (and possibly the libpcap0.8-dev if required).[/QUOTE]

hi,  i have instaled the libpcap 0.8 and 0.8-dev in the synaptic and continues give me that error :(

---

### Post by ape on 2006-01-17
okay, I see the issue.  libpcap0.8 and libpcap0.8-dev don't provide a libpcap.so.0 binary.  What you'll need to do is go into the /usr/lib directory and type `sudo ln -s libpcap.so.0.8.3 libpcap.so.0`.  This should create the necessary symlink for your source code to compile against.

---

### Post by lfvo on 2006-01-17
[QUOTE=ape]okay, I see the issue.  libpcap0.8 and libpcap0.8-dev don't provide a libpcap.so.0 binary.  What you'll need to do is go into the /usr/lib directory and type `sudo ln -s libpcap.so.0.8.3 libpcap.so.0`.  This should create the necessary symlink for your source code to compile against.[/QUOTE]

Thanks a lot, it works :D

---

