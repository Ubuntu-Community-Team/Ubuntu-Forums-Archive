---
title: "ipc error"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by bakwas on 2008-04-03
hi all,
i am trying to invoke a tool GUI but my system is not respoding faithfully. here is the o/p of "strace tool-name". Further it says in tool gui "waiting for ipc:0 to initiate"

*******************************************
ket(PF_INET, SOCK_DGRAM, IPPROTO_IP) = 472
connect(472, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("10.107.1.1")}, 28) = 0
fcntl64(472, F_GETFL)                   = 0x2 (flags O_RDWR)
fcntl64(472, F_SETFL, O_RDWR|O_NONBLOCK) = 0
gettimeofday({1207225188, 641660}, NULL) = 0
poll([{fd=472, events=POLLOUT, revents=POLLOUT}], 1, 0) = 1
send(472, "s~\1\0\0\1\0\0\0\0\0\0\17brajesh-desktop\4iit"..., 44, MSG_NOSIGNAL) = 44
poll([{fd=472, events=POLLIN, revents=POLLIN}], 1, 3000) = 1
ioctl(472, FIONREAD, [44])              = 0
recvfrom(472, "s~\201\203\0\1\0\0\0\0\0\0\17brajesh-desktop\4iit"..., 1024, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("10.107.1.1")}, [16]) = 44
close(472)                              = 0
open("/etc/mdns.allow", O_RDONLY)       = 472
fstat64(472, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f3f000
read(472, "", 4096)                     = 0
close(472)                              = 0
munmap(0xb6f3f000, 4096)                = 0
select(1, NULL, NULL, NULL, {0, 250000}


*******************************************

TIA

---

### Post by zvacet on 2008-04-03
**GUI = Graphical user interface**

If you have desktop version installed then GUI is runing.If you have problems with it type in **applications>accessories>terminal**

```
sudo /etc/init.d/gdm start
```

or 

**startx**

---

### Post by bakwas on 2008-04-03
hi,
i am able to get GUI of the said tool but due to "ipc" error machine is not able to open the tool properly. this does not include GUI under all circumstances.

---

