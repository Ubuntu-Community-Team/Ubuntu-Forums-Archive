---
title: "Help for Java Plugin for Firefox"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by RCB on 2006-01-17
Hello 
I have tried to install the Java plugin for firefox but don't know what the package is called in SMP. 
I have tried the manaul download too. :( 

Please help

---

### Post by rjwood on 2006-01-17
you just may want to use automatix by arnieboy. Search for it and ye shall find!!!

---

### Post by bfonseca on 2006-01-17
first i downloaded the jre from the java.sun.com and used the ark to unzip
when ark finished it left me with a folder: jre1.5.0_05

then i took the folder created by ark and mv that to /usr/local/

from here i did a search for all plugins and went to all of them and typed

ln -s /usr/bin/jdk/jdk1.5.0_05/jre/plugin/i386/ns7/libjavaplugin_oji.so

and i did this for every plugin...restart the borwser and try it again
it should work...hope this helps you.

Brian

---

### Post by RCB on 2006-01-17
Thanks rjwood and bfonseca.

automatix will not work I can't wget through the proxy firewall :(

I have copied to the /usr/local but how do I search for plugins and what do i link jave with?

thanks

---

### Post by mustang on 2006-01-17
Hello RCB,

the following two links will help you:

[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

[https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8](https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8)

The first relates to installing java, second relates to getting it to work with firefox. Please let us know if you encounter any problems.

---

