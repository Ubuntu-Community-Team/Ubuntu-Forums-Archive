---
title: "Installing Net-SNMP"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Wushu on 2008-04-01
I'm trying to install net-snmp 5.4.1 and I am hitting some big problems.

I read the install.txt - as below:

[I][SIZE="1"]QUICK INSTRUCTIONS
==================

  1) Run ./configure
     (type "./configure --help" for a quick usage summary.)
     (--prefix=PATH will change the default /usr/local installation path.)
     (see "Compilers and Options" on changing the compiler to use)

  2) Optionally edit include/net-snmp/net-snmp-config.h
     (due to prompting done by the configure script, this is very rarely
      necessary.)

  3) make

  4) Run the next command as root:
  5) make install

  6) configure the agent
     (either using 'snmpconf' or by crafting an snmpd.conf file manually.
      The file 'EXAMPLE.conf' may be a suitable starting point)

Note: By default, everything will be installed in /usr/local.
      (see below for more instructions)[/SIZE][/I]

I have ran through this a good few times , firstly got one or two problems but done the following sudo apt get installs -

libsnmp-base
snmp
libperl
libperl-dev
build-essential
-----
It now eventually goes through the basic install fine (from what i can see anyway) .. however whenever i try a command like snmpwalk i get 

"snmpwalk: error while loading shared libraries: libnetsnmp.so.15: cannot open shared object file: No such file or directory"

Any ideas?

---

### Post by Wushu on 2008-04-02
The above seems to have been fixed by a last ditched attempt at installing all the net-snmp package results from the synaptic package manager.

To be continued ..

---

### Post by mikecrowe on 2008-05-20
Wushu,

What did you find out?  I need to install 5.4.1 as well.

Mike

---

