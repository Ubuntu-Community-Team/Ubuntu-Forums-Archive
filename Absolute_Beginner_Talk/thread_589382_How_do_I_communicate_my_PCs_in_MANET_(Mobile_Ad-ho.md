---
title: "How do I communicate my PCs in MANET (Mobile Ad-hoc Network)"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by kyaw swar on 2007-10-24
This is my iwconfig and ifconfig..........
[COLOR="Navy"][COLOR="Navy"]
[COLOR="Navy"]manet@manet-laptop1:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"manet"
          Mode:Ad-Hoc  Frequency:2.432 GHz  Cell: 02:0F:B5:94:38:98
          Bit Rate:0 kb/s   Tx-Power=7 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
          Rx invalid nwid:35193  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1862  Invalid misc:1862   Missed beacon:0192.168.5.1

manet@manet-laptop1:~$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:94:3A:83
          inet addr:192.168.5.4  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe94:3a83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:184 errors:50677 dropped:0 overruns:0 frame:50677
          TX packets:184 errors:1869 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:17640 (17.2 KiB)  TX bytes:17640 (17.2 KiB)
          Interrupt:11 Memory:dec80000-dec90000[/COLOR][/COLOR][/COLOR]

I've set IP address and I can ping them in order. But what192.168.5.1 else I can proceed to communicate them or ensure that they can work peer to peer in Moblile Ad-HOc Network mode.

In addiction, this is the soft code named "fsrd", I've run (configure, make , make install). As follow the results.

manet@manet-laptop1:~/Desktop/fsrd$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/manet/Desktop/fsrd/missing: Unknown `--run' option
Try `/home/manet/Desktop/fsrd/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for pid_t... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking return type of signal handlers... void
checking for inet_ntoa... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strdup... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
manet@manet-laptop1:~/Desktop/fsrd$ sudo make
make  all-am
make[1]: Entering directory `/home/manet/Desktop/fsrd'
make[1]: Leaving directory `/home/manet/Desktop/fsrd'
manet@manet-laptop1:~/Desktop/fsrd$ sudo make install
make[1]: Entering directory `/home/manet/Desktop/fsrd'
/bin/sh ./mkinstalldirs /usr/local/bin
  /usr/bin/install -c fsrd /usr/local/bin/fsrd
make[1]: Nothing to be done for `install-data-am'.
make[1]: Leaving directory `/home/manet/Desktop/fsrd'


Please Kindly help me.
Regards.

---

