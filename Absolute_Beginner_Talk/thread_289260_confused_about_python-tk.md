---
title: "confused about python-tk"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by kaboom on 2006-10-30
I have a script that will allow me to connect to my university residential network and when i tried to use it i was told to install the python-tk package.  

i tried installing two versions; 2.4.1 and 2.4.3 from this site: [http://packages.ubuntulinux.org/hoary/python/python-tk](http://packages.ubuntulinux.org/hoary/python/python-tk)

for 2.4.1 the error came up 'dependency is not satisfiable: python2.4-tk

for 2.4.3 the error came up 'wrong architecture 'amd 64'


if it helps my machine is a hp pavillion dv4000

thanks in advance for your help

---

### Post by _lynX on 2006-10-30
Try the following command in the terminal:

*sudo aptitude install python-tk*

That should install your package, along with any dependencies that are needed.

---

### Post by kaboom on 2006-10-30
thanks for the quick reply.  

when i tried that i got a message saying 'couldn't find any package whose name or description matched python-tk.  i also tried it for the full name of the package to the same result.

based on the error messages i think its something wrong with what python-tk i'm downloading.

i didn't mention in the previous post that i'm using edgy.  so what python-tk do i need?

---

### Post by po0f on 2006-10-30
kaboom,

[This one](http://packages.ubuntu.com/edgy/python/python-tk).

---

### Post by kaboom on 2006-10-30
hey thanks for your help guys, i ended up figuring it out i needed to install some other dependencies first.

---

