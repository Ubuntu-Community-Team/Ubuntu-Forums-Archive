---
title: "need c compiler"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by vinther on 2006-07-12
Hi,

During installation of VMWare Workstation i received a message like "none of the installed modules are fit to run on your distribution - want to 'make' em?". Replying YES to this the installation was terminated with a message like "could not find the c compiler and/or make program"

Where can i find a c compiler, and are there special recommendation regarding the installation?

Thanks
Erik

---

### Post by Brunellus on 2006-07-12
sudo apt-get install build-essential

will get you everything you need.

---

### Post by vinther on 2006-07-12
perfect - thanks.

During compilation i'm prompted for the location of c header files that match the running kernel, and it not the default suggested /usr/src/linux/include?

Erik

---

### Post by fluffington on 2006-07-12
> **vinther said:**
> perfect - thanks.

During compilation i'm prompted for the location of c header files that match the running kernel, and it not the default suggested /usr/src/linux/include?

Erik

You also need to install the linux headers. And you'll probably want xinetd, too (it's required for networking in VMWare):

```
sudo apt-get install xinetd linux-headers-`uname -r`
```

---

### Post by vinther on 2006-07-12
sorry, should the the last bit be exactly?

'-uname -r'

---

### Post by vinther on 2006-07-12
works now (wrong `)

---

