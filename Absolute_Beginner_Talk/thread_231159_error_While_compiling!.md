---
title: "error While compiling!"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-08-07
Hi, I keep getting an error when I need to compile some programs from source.

This is what I get:

```
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
```

---

### Post by loell on 2006-08-07
i think you need xml parser module of perl, its downloadable via cpan

---

### Post by zxcvbnm on 2006-08-07
Sorry I am a newbie. What is cpan?

---

### Post by loell on 2006-08-07
or get libxml-parser-perl in apt

---

### Post by loell on 2006-08-07
ok, in command line just do

sudo apt-get install libxml-parser-perl

---

### Post by zxcvbnm on 2006-08-07
Ok thanks...I got it working.



-thanks

---

