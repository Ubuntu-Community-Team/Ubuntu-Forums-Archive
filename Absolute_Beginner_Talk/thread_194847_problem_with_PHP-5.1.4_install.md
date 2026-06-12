---
title: "problem with PHP-5.1.4 install"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by finch on 2006-06-12
Hi, i`m new in linux.
Here what i get when try to install php5 as root acc

Ubuntu 5.10

```

root@finch:/home/finch/php-5.1.4# ./configure
loading cache ./config.cache
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
configure: warning: bison versions supported for regeneration of the Zend/PHP parsers: 1.28 1.35 1.75 1.875 2.0 2.1 (found: none).
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 3246: lex: command not found
configure: error: cannot find output from lex; giving up
root@finch:/home/finch/php-5.1.4#

```
Can you help me, where the problem could be?

---

### Post by fluffington on 2006-06-12
It looks like you don't have re2c, bison, or lex. That's easily fixed, though:

```
sudo apt-get install re2c bison flex
```

Also, why not just install Ubuntu's php5 package?

---

