---
title: "Trouble Compiling Software from Source (TOR)"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by mfmbcpman on 2007-09-02
I am trying to install TOR but I am coming across one error involving libevent but I don't know what to do.

```
michael@olddell:~/Desktop/tor-0.1.2.17$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for win32... no
checking for MIPSpro compiler... no
checking for library containing socket... none required
checking for library containing gethostbyname... none required
checking for library containing dlopen... -ldl
checking for library containing inet_aton... none required
checking for library containing pthread_create... -lpthread
checking for library containing pthread_detach... none required
checking for gettimeofday... yes
checking for ftime... yes
checking for socketpair... yes
checking for uname... yes
checking for inet_aton... yes
checking for strptime... yes
checking for getrlimit... yes
checking for strlcat... no
checking for strlcpy... no
checking for strtoull... yes
checking for ftello... yes
checking for getaddrinfo... yes
checking for localtime_r... yes
checking for gmtime_r... yes
checking for memmem... yes
checking for strtok_r... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_create... yes
checking for u_int64_t... yes
checking for u_int32_t... yes
checking for u_int16_t... yes
checking for u_int8_t... yes
checking for libevent directory... configure: error: Could not find a linkable libevent. You can specify an explicit path using --with-libevent-dir

```

---

### Post by badactress on 2007-09-02
You could try:

sudo apt-get install libevent1 libevent-dev

---

