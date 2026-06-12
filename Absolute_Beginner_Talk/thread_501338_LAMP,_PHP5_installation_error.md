---
title: "LAMP, PHP5 installation error"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-07-15
i downloaded sources for amp, and trying to install it, apache installed successfully but PHP is giving some problems:

```

//installing PHP5
shoaibi@golden-eagle:~$ cd php-5.2.3/
shoaibi@golden-eagle:~/php-5.2.3$ ./configure --with-apxs2=/usr/local/apache2/bin/apxs 
creating cache ./config.cache
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for icc... no
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking whether ln -s works... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for re2c... no
configure: warning: You will need re2c 0.9.11 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for bison... no
checking for byacc... no
checking for bison version... invalid
configure: warning: bison versions supported for regeneration of the Zend/PHP parsers: 1.28 1.35 1.75 1.875 2.0 2.1 2.2 2.3 (found: none).
checking for flex... lex
checking for yywrap in -ll... no
checking for working const... yes
configure: warning: flex versions supported for regeneration of the Zend/PHP parsers: 2.5.4  (found: none).
checking whether to force non-PIC code in shared modules... yes
checking whether /dev/urandom exists... yes
checking for pthreads_cflags... -pthread
checking for pthreads_lib... 

Configuring SAPI modules
checking for AOLserver support... no
checking for Apache 1.x module support via DSO through APXS... no
checking for Apache 1.x module support... no
checking for mod_charset compatibility option... no
checking for Apache 2.0 filter-module support via DSO through APXS... no
checking for Apache 2.0 handler-module support via DSO through APXS... yes
checking for Apache 1.x (hooks) module support via DSO through APXS... no
checking for Apache 1.x (hooks) module support... no
checking for mod_charset compatibility option... no
checking for Caudium support... no
checking for CLI build... yes
checking for Continuity support... no
checking for embedded SAPI library support... no
checking for Zeus ISAPI support... no
checking for Milter support... no
checking for NSAPI support... no
checking for PHTTPD support... no
checking for Pi3Web support... no
checking for Roxen/Pike support... no
checking for thttpd... no
checking for TUX... no
checking for webjames... no
checking for chosen SAPI module... apache2handler

Running system checks
checking for sendmail... no
checking whether system uses EBCDIC... no
checking whether byte ordering is bigendian... no
checking whether writing to stdout works... This is the test message -- yes
checking for socket... yes
checking for socketpair... yes
checking for htonl... yes
checking for gethostname... yes
checking for gethostbyaddr... yes
checking for yp_get_default_domain... no
checking for __yp_get_default_domain... no
checking for yp_get_default_domain in -lnsl... yes
checking for dlopen... no
checking for __dlopen... no
checking for dlopen in -ldl... yes
checking for sin in -lm... yes
checking for res_search... no
checking for __res_search... no
checking for res_search in -lresolv... yes
checking for inet_aton... yes
checking for dn_skipname... no
checking for __dn_skipname... yes
checking for ANSI C header files... yes
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for inttypes.h... yes
checking for stdint.h... yes
checking for dirent.h... yes
checking for ApplicationServices/ApplicationServices.h... no
checking for sys/param.h... yes
checking for sys/types.h... yes
checking for sys/time.h... yes
checking for netinet/in.h... yes
checking for alloca.h... yes
checking for arpa/inet.h... yes
checking for arpa/nameser.h... yes
checking for assert.h... yes
checking for crypt.h... yes
checking for fcntl.h... yes
checking for grp.h... yes
checking for ieeefp.h... no
checking for langinfo.h... yes
checking for limits.h... yes
checking for locale.h... yes
checking for monetary.h... yes
checking for mach-o/dyld.h... no
checking for netdb.h... yes
checking for pwd.h... yes
checking for resolv.h... yes
checking for signal.h... yes
checking for stdarg.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for syslog.h... yes
checking for sysexits.h... yes
checking for sys/ioctl.h... yes
checking for sys/file.h... yes
checking for sys/mman.h... yes
checking for sys/mount.h... yes
checking for sys/poll.h... yes
checking for sys/resource.h... yes
checking for sys/select.h... yes
checking for sys/socket.h... yes
checking for sys/statfs.h... yes
checking for sys/statvfs.h... yes
checking for sys/vfs.h... yes
checking for sys/sysexits.h... no
checking for sys/varargs.h... no
checking for sys/wait.h... yes
checking for sys/loadavg.h... no
checking for termios.h... yes
checking for unistd.h... yes
checking for unix.h... no
checking for utime.h... yes
checking for sys/utsname.h... yes
checking for sys/ipc.h... yes
checking for dlfcn.h... yes
checking for assert.h... (cached) yes
checking for fopencookie... yes
checking for broken getcwd... no
checking for broken libc stdio... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for tm_zone in struct tm... yes
checking for missing declarations of reentrant functions... done
checking for fclose declaration... ok
checking for tm_gmtoff in struct tm... yes
checking for struct flock... yes
checking for socklen_t... yes
checking size of intmax_t... 0
checking size of size_t... 4
checking size of ssize_t... 0
checking size of ptrdiff_t... 0
checking size of long long... 8
checking size of long long int... 8
checking size of long... 4
checking size of int... 4
checking for st_blksize in struct stat... yes
checking for st_blocks in struct stat... yes
checking for st_rdev in struct stat... yes
checking for size_t... yes
checking for uid_t in sys/types.h... yes
checking for struct sockaddr_storage... yes
checking for field sa_len in struct sockaddr... no
checking for IPv6 support... yes
checking for vprintf... yes
checking for alphasort... yes
checking for asctime_r... yes
checking for chroot... yes
checking for ctime_r... yes
checking for cuserid... yes
checking for crypt... no
checking for flock... yes
checking for ftok... yes
checking for funopen... no
checking for gai_strerror... yes
checking for gcvt... yes
checking for getloadavg... yes
checking for getlogin... yes
checking for getprotobyname... yes
checking for getprotobynumber... yes
checking for getservbyname... yes
checking for getservbyport... yes
checking for getrusage... yes
checking for gettimeofday... yes
checking for gmtime_r... yes
checking for getpwnam_r... yes
checking for getgrnam_r... yes
checking for getpwuid_r... yes
checking for grantpt... yes
checking for inet_ntoa... yes
checking for inet_ntop... yes
checking for inet_pton... yes
checking for isascii... yes
checking for link... yes
checking for localtime_r... yes
checking for lockf... yes
checking for lchown... yes
checking for lrand48... yes
checking for memcpy... yes
checking for memmove... yes
checking for mkstemp... yes
checking for mmap... yes
checking for nl_langinfo... yes
checking for perror... yes
checking for poll... yes
checking for ptsname... yes
checking for putenv... yes
checking for realpath... yes
checking for random... yes
checking for rand_r... yes
checking for regcomp... yes
checking for res_search... (cached) yes
checking for scandir... yes
checking for setitimer... yes
checking for setlocale... yes
checking for localeconv... yes
checking for setenv... yes
checking for setpgid... yes
checking for setsockopt... yes
checking for setvbuf... yes
checking for shutdown... yes
checking for sin... yes
checking for snprintf... yes
checking for srand48... yes
checking for srandom... yes
checking for statfs... yes
checking for statvfs... yes
checking for std_syslog... no
checking for strcasecmp... yes
checking for strcoll... yes
checking for strdup... yes
checking for strerror... yes
checking for strftime... yes
checking for strptime... yes
checking for strstr... yes
checking for strtok_r... yes
checking for symlink... yes
checking for tempnam... yes
checking for tzset... yes
checking for unlockpt... yes
checking for unsetenv... yes
checking for usleep... yes
checking for nanosleep... yes
checking for utime... yes
checking for vsnprintf... yes
checking for getaddrinfo... yes
checking for strlcat... no
checking for strlcpy... no
checking for getopt... yes
checking whether utime accepts a null argument... yes
checking for working alloca.h... (cached) yes
checking for alloca... yes
checking for declared timezone... yes
checking for type of reentrant time-related functions... POSIX
checking for readdir_r... yes
checking for type of readdir_r... POSIX
checking for in_addr_t... yes
checking for crypt_r... no

General settings
checking whether to include gcov symbols... no
checking whether to include debugging symbols... no
checking layout of installed files... PHP
checking path to configuration file... DEFAULT
checking where to scan for configuration files... DEFAULT
checking whether to enable safe mode by default... no
checking for safe mode exec dir... /usr/local/php/bin
checking whether to enable PHP's own SIGCHLD handler... no
checking whether to enable magic quotes by default... no
checking whether to enable runpaths... yes
checking whether to explicitly link against libgcc... no
checking whether to enable short tags by default... yes
checking whether to enable dmalloc... no
checking whether to enable IPv6 support... yes
checking how big to make fd sets... using system default
checking whether to enable versioning... no

Configuring extensions
checking whether to enable LIBXML support... yes
checking libxml2 install dir... no
checking for xml2-config path... 
configure: error: xml2-config not found. Please check your libxml2 installation.
shoaibi@golden-eagle:~/php-5.2.3$ make
make: *** No targets specified and no makefile found.  Stop.
shoaibi@golden-eagle:~/php-5.2.3$ sudo make install
make: *** No rule to make target `install'.  Stop.
shoaibi@golden-eagle:~/php-5.2.3$ 

```


please don't suggest an online installation or xampp

---

### Post by DBStevens on 2007-07-15
"checking whether to enable LIBXML support... yes
checking libxml2 install dir... no"

You need to install the package for libxml2  your configuration failed so there was no make file to do the next steps.

Why can't you do an online install from the repos?

---

