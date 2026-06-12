---
title: "how to install java"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by lakinbrian on 2008-02-04
Hi 
I might be a bit old for ubuntu but a friend load me a copy of 7.10 which I have now installed but when I try to install programes it says unable to install such as Realplay for my radio programes ect all ask for java so I went to the java site only to be confronted with 4 linux downloads I downloaded 6u3-linux-i586.bin and when try to open it this comes up Unhandled MIME type: “application/x-shellscript”

any help please

---

### Post by hyper_ch on 2008-02-04
you install java using synaptic... use Sun Java

---

### Post by Ub1476 on 2008-02-04
HI, for Linux you usually wont have to browse the web for certain apps. Just open Add/Remove and search for "ubuntu restricted extras". That package contains codecs, java, flash etc. If you want to install java only, search for "jre".

---

### Post by SOULRiDER on 2008-02-04
The package is called
sun-java6-jre

You can also install it from a terminal using this command
```
sudo aptitude install sun-java6-jre
```
That will automatically download and install java.

---

### Post by jan quark on 2008-02-04
I always install these packages

```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

---

