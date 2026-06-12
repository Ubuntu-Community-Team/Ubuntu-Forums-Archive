---
title: "[SOLVED] Php configure error help please"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by appleimac on 2008-03-01
Hi there I am trying to install php 4.4.8 in my server.

I am running this command

```
[root@webserver php-4.4.8]# ./configure --with-apxs=/usr/local/apache/bin/apxs --disable-debug --enable-ftp --enable-inline-optimization --enable-magic-quotes --enable-mbstring --enable-mm=shared --enable-safe-mode --enable-track-vars --enable-trans-sid --enable-wddx=shared --enable-xml --with-dom --with-gd --with-gettext --with-mysql=/usr/local/mysql --with-regex=system --with-xml --with-zlib-dir=/usr/lib
```


But I get this output

```
loading cache ./config.cache
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for re2c... exit 0;
checking whether ln -s works... yes
checking for gawk... gawk
checking for bison... no
checking for byacc... no
configure: warning: You will need bison if you want to regenerate the PHP parsers.
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for working const... yes
checking flex version... 2.5.4 (ok)
checking whether byte ordering is bigendian... no
checking whether to force non-PIC code in shared modules... no
checking for pthreads_cflags... -pthread
checking for pthreads_lib... 

Configuring SAPI modules
checking for AOLserver support... no
checking for Apache 1.x module support via DSO through APXS... configure: error: You have enabled Apache 1.3 support while your server is Apache 2.  Please use the appropiate switch --with-apxs2
```


Any help would be great

---

### Post by kinghowdy on 2008-03-01
Good Morning,

I'm not 100% sure on this but just by reading what you posted try 

./configure --with-apxs**2**=/usr/local/apache/bin/apxs --disable-debug --enable-ftp --enable-inline-optimization --enable-magic-quotes --enable-mbstring --enable-mm=shared --enable-safe-mode --enable-track-vars --enable-trans-sid --enable-wddx=shared --enable-xml --with-dom --with-gd --with-gettext --with-mysql=/usr/local/mysql --with-regex=system --with-xml --with-zlib-dir=/usr/lib

The last line where you get the error says: 
Please use the appropiate switch --with-apxs2

So give that a go and see what happens. Is there a reason why you are not trying to install PHP/Apache through Synaptic?

---

### Post by appleimac on 2008-03-01
HI thanks that worked but when I no runt he command 

```
make && make install
```

I get this output error.

```
/usr/bin/ld: /usr/local/mysql/lib/mysql/libz.a(adler32.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/mysql/lib/mysql/libz.a(adler32.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libphp4.la] Error 1


```


Any Ideas?

---

### Post by appleimac on 2008-03-01
Sorry for the bump but I need to get this working.

Any Ideas guys?

EDIT: I have solved the problem by installing php5

---

### Post by fahadsadah on 2008-05-18
```
sudo apt-get install php5
```
I know this is a bit late, I'm sorry.

---

