---
title: "kernel sources"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by topa on 2005-09-03
Hello, I am new to ubuntu and I'm trying to install some driver for my modem but when I execute the ./configure command it tells me at the end it could not find the kernel sources. Where can I find them and how do I best install them.

thanks
tony

---

### Post by woifi on 2005-09-03
first of all, you're not in the right forum ;)

anyway, you have to install your kernel sources:
type ```
uname -r
``` in your console to check which kernel-image is installed and then install your sources with ```
apt-get install linux-source-2.6.10
``` ... if you have 2.6.10 installed

hth

woifi

---

### Post by N'Jal on 2005-09-03
try 
```

sudo apt-get install linux-source-2.6.10

```

You could use 2.6.11 but the offiial kernel used by hoary is 2.6.10, i get the feeling that the thing will ask you to recompile your kernel.

---

### Post by topa on 2005-09-03
Thanks for the answer and sorry for being in the wrong forum

tony

---

### Post by topa on 2005-09-04
First of all I want to ask if someone can put this in the right forum.
Second, I did apt-get install linux-sources-2.6.10 because after a uname -r it tells me 2.6.10-2-686
but I keep on having the same problem, while trying to ./cofigure the eagle-usb 2.1.1 it tells me: 'Kernel sources not found' although I didn't have a problem after the apt-get install linux-sources-2.6.10

tony

---

### Post by az on 2005-09-04
[QUOTE=topa]First of all I want to ask if someone can put this in the right forum.
Second, I did apt-get install linux-sources-2.6.10 because after a uname -r it tells me 2.6.10-2-686
but I keep on having the same problem, while trying to ./cofigure the eagle-usb 2.1.1 it tells me: 'Kernel sources not found' although I didn't have a problem after the apt-get install linux-sources-2.6.10

tony[/QUOTE]
How did you install ubuntu?  Did you use a preview cd?

2.6.10-2 is not the released kernel.  The Hoary kernel is 2.6.10-5.  Update your kernel and install the linux-headers package for it.  You do not need the source, just the headers.

---

### Post by topa on 2005-09-05
I installed it from a DVD which was witha linux magazine.

thanks for the advise
tony

---

