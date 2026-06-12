---
title: "Manual Install Trouble"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by slayer456 on 2006-12-15
Hey guys, im a total noob at Ubuntu and Linux in general so I need some help here. I keep on downloading these tarball file and trying to install them, but they never work. I get to the "make" command and the console gets flooded with errors messages and such. It doesnt let me finish the install at all. I really need help resolving this problem. Please help me somebody.

---

### Post by taurus on 2006-12-15
If you want to build something from source, you need the build-essential package...

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```
Otherwise, read this guide for installing software on Ubuntu.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by slayer456 on 2006-12-15
Thanks but sorry, neither helped, this is really frusturating me. I did all the first steps (I think ) and type the make command and this is  only a bit of what comes up:

siplib.c:7063: error: syntax error before &#8216;sipSigArg&#8217;
siplib.c: In function &#8216;sipFindSigArgType&#8217;:
siplib.c:7065: error: &#8216;em&#8217; undeclared (first use in this function)
siplib.c:7066: error: &#8216;po&#8217; undeclared (first use in this function)
siplib.c:7068: error: &#8216;at&#8217; undeclared (first use in this function)
siplib.c:7078: error: &#8216;name&#8217; undeclared (first use in this function)
siplib.c:7078: error: &#8216;len&#8217; undeclared (first use in this function)
siplib.c:7080: error: &#8216;tem&#8217; undeclared (first use in this function)
siplib.c:7106: error: &#8216;indir&#8217; undeclared (first use in this function)
siplib.c: At top level:
siplib.c:7206: error: syntax error before &#8216;*&#8217; token
siplib.c: In function &#8216;sip_api_register_int_types&#8217;:
siplib.c:7208: error: &#8216;po&#8217; undeclared (first use in this function)
siplib.c:7212: error: &#8216;args&#8217; undeclared (first use in this function)
siplib.c:7228: error: &#8216;PyExc_TypeError&#8217; undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}:130: Error: symbol `sipQtSupport' is already defined
{standard input}:136: Error: symbol `sipInterpreter' is already defined
make[1]: *** [siplib.o] Error 1
make[1]: Leaving directory `/home/anthony/sip-4.5.2/siplib'
make: *** [all] Error 2

Thanks for trying. If its just my insolence that made me skip something, im sorry.

---

### Post by taurus on 2006-12-15
So "./configure" ran fine!!!

---

### Post by slayer456 on 2006-12-15
yes, it went through all the normal procedures

---

### Post by Sef on 2006-12-15
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by slayer456 on 2006-12-15
ok, I finally got it to work through synaptic so i guess I eally should have looked first before making a useless topic. Sorry guys, but thanks for your help.

---

