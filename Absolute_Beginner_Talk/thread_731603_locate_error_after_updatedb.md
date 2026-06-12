---
title: "locate error after updatedb"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by mokkai on 2008-03-22
fax@ubuntu7.04:~/Desktop/Rails_2/blog$ locate /usr/*/mkmf.log
locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old
/usr/lib/ruby/gems/1.8/gems/mongrel-1.1.4/ext/http11/mkmf.log
/usr/lib/ruby/gems/1.8/gems/termios-0.9.4/mkmf.log
/usr/lib/ruby/gems/1.8/gems/mongrel-1.0.1/ext/http11/mkmf.log
/usr/lib/ruby/gems/1.8/gems/rmagick-2.2.2/ext/RMagick/mkmf.log

fax@ubuntu7.04:~/Desktop/Rails_2/blog$ sudo updatedb

fax@ubuntu7.04:~/Desktop/Rails_2/blog$ locate /usr/*/mkmf.log
/usr/lib/ruby/gems/1.8/gems/mongrel-1.1.4/ext/http11/mkmf.log
/usr/lib/ruby/gems/1.8/gems/termios-0.9.4/mkmf.log
/usr/lib/ruby/gems/1.8/gems/mongrel-1.0.1/ext/http11/mkmf.log
/usr/lib/ruby/gems/1.8/gems/mysql-2.7/mkmf.log
/usr/lib/ruby/gems/1.8/gems/rmagick-2.2.2/ext/RMagick/mkmf.log
*** glibc detected *** locate: double free or corruption (fasttop): 0x08052850 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e737cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e76e30]
locate[0x804b149]
locate[0x804af63]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7e21ebc]
locate[0x80492e1]
======= Memory map: ========
08048000-08050000 r-xp 00000000 08:0e 1619786    /usr/bin/slocate
08050000-08051000 rw-p 00007000 08:0e 1619786    /usr/bin/slocate
08051000-08072000 rw-p 08051000 00:00 0          [heap]
b7c00000-b7c21000 rw-p b7c00000 00:00 0 
b7c21000-b7d00000 ---p b7c21000 00:00 0 
b7dd6000-b7ddf000 r-xp 00000000 08:05 407573     /lib/tls/i686/cmov/libnss_files-2.5.so
b7ddf000-b7de1000 rw-p 00008000 08:05 407573     /lib/tls/i686/cmov/libnss_files-2.5.so
b7de1000-b7de9000 r-xp 00000000 08:05 407577     /lib/tls/i686/cmov/libnss_nis-2.5.so
b7de9000-b7deb000 rw-p 00007000 08:05 407577     /lib/tls/i686/cmov/libnss_nis-2.5.so
b7deb000-b7dfe000 r-xp 00000000 08:05 407567     /lib/tls/i686/cmov/libnsl-2.5.so
b7dfe000-b7e00000 rw-p 00012000 08:05 407567     /lib/tls/i686/cmov/libnsl-2.5.so
b7e00000-b7e02000 rw-p b7e00000 00:00 0 
b7e02000-b7e09000 r-xp 00000000 08:05 407569     /lib/tls/i686/cmov/libnss_compat-2.5.so
b7e09000-b7e0b000 rw-p 00006000 08:05 407569     /lib/tls/i686/cmov/libnss_compat-2.5.so
b7e0b000-b7e0c000 rw-p b7e0b000 00:00 0 
b7e0c000-b7f47000 r-xp 00000000 08:05 407556     /lib/tls/i686/cmov/libc-2.5.so
b7f47000-b7f48000 r--p 0013b000 08:05 407556     /lib/tls/i686/cmov/libc-2.5.so
b7f48000-b7f4a000 rw-p 0013c000 08:05 407556     /lib/tls/i686/cmov/libc-2.5.so
b7f4a000-b7f4d000 rw-p b7f4a000 00:00 0 
b7f51000-b7f5c000 r-xp 00000000 08:05 373952     /lib/libgcc_s.so.1
b7f5c000-b7f5d000 rw-p 0000a000 08:05 373952     /lib/libgcc_s.so.1
b7f5d000-b7f60000 rw-p b7f5d000 00:00 0 
b7f60000-b7f79000 r-xp 00000000 08:05 373909     /lib/ld-2.5.so
b7f79000-b7f7b000 rw-p 00019000 08:05 373909     /lib/ld-2.5.so
bfbf0000-bfc06000 rw-p bfbf0000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted
fax@ubuntu7.04:~/Desktop/Rails_2/blog$

anyway i got what i want (/usr/lib/ruby/gems/1.8/gems/mysql-2.7/mkmf.log)
but why its Aborted at last ?

---

### Post by mattismyname on 2008-03-22
That definitely looks like a bug in locate to me.  I would report it in launchpad.

---

