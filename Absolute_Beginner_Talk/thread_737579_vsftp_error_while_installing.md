---
title: "vsftp error while installing"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by psychobeauty on 2008-03-27
each time that im trying to install vsftp or proftp i get this error...why???:mad:



```
gcc -c main.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c utility.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c prelogin.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c ftpcmdio.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c postlogin.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c privsock.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c tunables.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c ftpdataio.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c secbuf.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c ls.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c postprivparent.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c logging.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c str.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c netstr.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c sysstr.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c strlist.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c banner.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c filestr.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c parseconf.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c secutil.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c ascii.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c oneprocess.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c twoprocess.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c privops.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c standalone.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c hash.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c tcpwrap.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c ipaddrparse.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c access.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c features.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c readwrite.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c opts.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c ssl.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c sysutil.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
gcc -c sysdeputil.c -O2 -Wall -W -Wshadow  -idirafter dummyinc
sysdeputil.c:162: error: expected declaration specifiers or ‘...’ before ‘capset’
sysdeputil.c:162: error: expected declaration specifiers or ‘...’ before ‘header’
sysdeputil.c:162: error: expected declaration specifiers or ‘...’ before ‘data’
In file included from sysdeputil.c:170:
/usr/include/sys/sendfile.h: In function ‘_syscall2’:
/usr/include/sys/sendfile.h:35: error: storage class specified for parameter ‘sendfile’
sysdeputil.c:186: error: storage class specified for parameter ‘environ’
sysdeputil.c:187: error: storage class specified for parameter ‘s_proctitle_space’
sysdeputil.c:187: error: parameter ‘s_proctitle_space’ is initialized
sysdeputil.c:188: error: storage class specified for parameter ‘s_proctitle_inited’
sysdeputil.c:188: error: parameter ‘s_proctitle_inited’ is initialized
sysdeputil.c:189: error: storage class specified for parameter ‘s_p_proctitle’
sysdeputil.c:189: error: parameter ‘s_p_proctitle’ is initialized
sysdeputil.c:201: error: storage class specified for parameter ‘do_sendfile’
sysdeputil.c:202: error: storage class specified for parameter ‘vsf_sysutil_setproctitle_internal’
sysdeputil.c:203: error: storage class specified for parameter ‘s_proctitle_prefix_str’
sysdeputil.c:215: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:436: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:474: error: storage class specified for parameter ‘do_checkcap’
sysdeputil.c:478: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:497: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:514: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:527: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:604: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:641: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:796: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:803: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:809: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:856: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:889: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:930: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:935: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:976: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:1012: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:1128: error: storage class specified for parameter ‘s_uwtmp_inserted’
sysdeputil.c:1129: error: storage class specified for parameter ‘s_utent’
sysdeputil.c:1134: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:1173: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
sysdeputil.c:1189: error: old-style parameter declarations in prototyped function definition
sysdeputil.c:162: error: parameter name omitted
sysdeputil.c:162: error: parameter name omitted
sysdeputil.c:162: error: parameter name omitted
sysdeputil.c:1189: error: expected ‘{’ at end of input
make: *** [sysdeputil.o] Error 1

```

---

### Post by talsemgeest on 2008-03-28
I would take a guess that there is a problem with the code.

---

### Post by cisforcojo on 2008-03-28
Are you trying to install FTP clients, because the daemons for both of those programs are in synaptic. It appears like there's a problem with the actual source.

---

### Post by psychobeauty on 2008-03-28
> **talsemgeest said:**
> I would take a guess that there is a problem with the code.




what u mean??


i tried quite a lot times to install it..and i download the package from different websites
but always the same problemwhen i try to install any ftp!!

---

