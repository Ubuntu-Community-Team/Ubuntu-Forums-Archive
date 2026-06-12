---
title: "why &quot;Make&quot; doenst work for me ?"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by medya on 2006-04-20
I want to install a very small program by source, but It is killing me.

the program name is Netspeed, I downloaded it from gnome files . it is a program to show your internet speed.

I do this :
1- extract the program
2-fred@ubuntu:~/Desktop$ cd nets*

3-then I run configure
[COLOR="Gray"]fred@ubuntu:~/Desktop/netspeed_applet-0.13$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.33 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is require d for intltool
[/COLOR]

4- then I run make and sudo make install
fred@ubuntu:~/Desktop/netspeed_applet-0.13$ make
make: *** No targets specified and no makefile found.  Stop.

fred@ubuntu:~/Desktop/netspeed_applet-0.13$ sudo make install
make: *** No rule to make target `install'.  Stop.
fred@ubuntu:~/Desktop/netspeed_applet-0.13$



why it doesnt work ? 
i have the same problem for many other programs

---

### Post by unbuntu on 2006-04-20
configure wasn't successful:

> 
checking for XML::Parser... configure: error: XML::Parser perl module is require d for intltool


It's a Perl package, download it from CPAN

---

### Post by netkid91 on 2006-04-20
And if you don't know how, it's simple.  Run the command:
```

sudo perl -MCPAN -e shell

```
Then type in
```

install XML::Parser

```
Assuming you have build-essentail installed, than you have everything to compile this module and it's dependincies(bad spelling, I know).

---

### Post by Hallavej on 2006-04-20
dont no why it doesnt work but why install from source.
sudo apt-get install netspeed
is all you need

---

### Post by unbuntu on 2006-04-20
[QUOTE=Hallavej]dont no why it doesnt work but why install from source.
sudo apt-get install netspeed
is all you need[/QUOTE]

Sometimes it's necessary to install from source.  Not every software comes with a package.

---

### Post by Mustard on 2006-04-20
Actually for the majority of the perl modules, you will find an equivalent perl package in the repositories.  For  XML::Parser perl module, you would install this package using apt-get..

```
sudo apt-get install libxml-parser-perl
```

It's not really necessary to get the modules from CPAN. The packages usually following the naming convention of *lib(name of perl-module)-perl*

---

