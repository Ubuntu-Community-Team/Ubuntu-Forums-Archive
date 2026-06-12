---
title: "unable to compile modem drivers in feisty"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by dckirba on 2007-04-23
Hello all,

I have a smartlink modem which uses the slamr driver. I have used this modem successfully in dapper, but have so far had no success compiling the drivers in feisty.

I have installed kernel headers and build-essential. The process I&#7743; following is based on the wiki howto which has served me perfectly well till date.

I have to install the ungrab-winmodem thingy from the linmodems site, but this is the output I get when I type make:

```
david@ChomonKora:~/Desktop/ungrab-winmodem$ sudo make
Password:
make modules -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/david/Desktop/ungrab-winmodem
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/david/Desktop/ungrab-winmodem/ungrab-winmodem.o
/home/david/Desktop/ungrab-winmodem/ungrab-winmodem.c:14:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/david/Desktop/ungrab-winmodem/ungrab-winmodem.o] Error 1
make[1]: *** [_module_/home/david/Desktop/ungrab-winmodem] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2
david@ChomonKora:~/Desktop/ungrab-winmodem$ 
```

The modem driver won work unless ungrab-winmodem is installed so I&#7743; basically stuck at this step.

I am sorry for cross posting, bu Ie searched everywhere and have found no solution and I really need my modem working. And I&#7743; clueless as to what might be wrong. 

So thanks in advance,

Regards,
David K

---

### Post by ad0 on 2007-04-23
There is allways problems with linux/config.h. Try to replace the headers. There is also a link that might help you.

[http://tuxx-home.at/archives/2007/04/10/T15_55_43/]("http://tuxx-home.at/archives/2007/04/10/T15_55_43/")

Hope it helps you.

[email]mustafic@xxxxx.com[/email]

---

### Post by dckirba on 2007-04-23
Thanks ado,

I received help on teh networking and wireless forum and everything now compiles:

[http://ubuntuforums.org/showthread.php?p=2518977#post2518977]("http://ubuntuforums.org/showthread.php?p=2518977#post2518977")

Thanks again,
David K

---

