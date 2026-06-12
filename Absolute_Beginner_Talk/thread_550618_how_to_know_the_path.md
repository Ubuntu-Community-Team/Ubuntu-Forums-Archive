---
title: "how to know the path"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by munna_dude on 2007-09-14
hi all
i am looking this strange..
this querry about xulrunner..
how to know the  xulrunner is installed or not..
i tried this
```

rpm -q xulrunner

```
and the output is 
> 
package xulrunner is not installed


actually i would like to know ".so" file path of current xulrunner
means
```

rpm -ql xulrunner | grep moz.so

```

can you please help me to find the path of libgtkembedmoz.so of xulrunner

thank you in advance

---

### Post by splintercellguy on 2007-09-14
Why are you trying to install xulrunner using RPM? Ubuntu uses the APT packaging system; you may either use the Synaptic GUI to install APT packages, or you may use the command-line apt-get/aptitude. In your case, I presume you want to do:

sudo apt-get install xulrunner

---

### Post by munna_dude on 2007-09-14
> **splintercellguy said:**
> Why are you trying to install xulrunner using RPM? Ubuntu uses the APT packaging system; you may either use the Synaptic GUI to install APT packages, or you may use the command-line apt-get/aptitude. In your case, I presume you want to do:

sudo apt-get install xulrunner

thank you i did the same..

but how to know the libgtkembedmoz.so path for xulrunner..
am asking about path....

please help me 

thank you in advance

---

### Post by chuckyp on 2007-09-14
Open a terminal and 
```

$ locate libgtkembedmoz.so

```
If you just installed the program you may have to update yoru data base to use locate with:
```

$ sudo updatedb

```

---

### Post by munna_dude on 2007-09-14
> **chuckyp said:**
> Open a terminal and 
```

$ locate libgtkembedmoz.so

```
If you just installed the program you may have to update yoru data base to use locate with:
```

$ sudo updatedb

```

thank you is there any command other than locate...
please help me 

thank you in advance

---

### Post by chuckyp on 2007-09-14
locate is part of the slocate package.  It is used to locate files on your system.

---

### Post by hyper_ch on 2007-09-14
you could also use "find"

---

### Post by munna_dude on 2007-09-14
> **chuckyp said:**
> locate is part of the slocate package.  It is used to locate files on your system.

yes.
it is working in Ubuntu, fedora..
but locate is not working for suse10.3

how to find the path...
is there any other way to locate the path..

please help me 

thank you in advance

---

### Post by hyper_ch on 2007-09-14
see the post above your last one ;)

---

### Post by kombipom on 2007-09-14
find / -name "libgtkembedmoz.so"

expect a lot of messages about directories it can't search.  Is ther a quiet flag in find?

---

