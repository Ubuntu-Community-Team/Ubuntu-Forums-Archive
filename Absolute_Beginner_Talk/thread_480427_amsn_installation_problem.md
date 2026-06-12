---
title: "amsn installation problem"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by pandoratomorrow on 2007-06-21
Hello.

I'm trying to install amsn, but I get a problem. (See attached image) What should I do?

Thanks.

---

### Post by phr0ze on 2007-06-21
> **pandoratomorrow said:**
> Hello.

I'm trying to install amsn, but I get a problem. (See attached image) What should I do?

Thanks.

Go into synaptic (System->Administration) and do a search for the missing package. Then check it off and install it.

---

### Post by pandoratomorrow on 2007-06-21
Okay. Where should I put the package, when I've installed it?

---

### Post by freshmeatz on 2007-06-21
do what other user said, but search for amsn

select file in synaptic and do a properties, move to deps tab

see what it requires, looks like tcl 8.4 to me

dont put it anywhere , just install it , or let synaptics, install the whole amsn set for you. i just looked myself , even though im not a msn user.
or if you just downloaded it , hopefully a .deb , make sure synaptic is closed and click the file to open and install. once file is installed you dont really need the *.deb anymore

---

### Post by phr0ze on 2007-06-21
Everything will be taken care of for you. Have you tried searching for AMSN in synaptic first. If its there, all you have to do is check the box and click apply at the top. Synaptic will auto install all needed components and put everything where it belongs.

---

### Post by zerobinary on 2007-06-21
well try this sudo apt-get install tcl8.4

---

### Post by freshmeatz on 2007-06-21
> **zerobinary said:**
> well try this sudo apt-get install tcl8.4

that should work for you, but when installing stuff it is best to use synaptic , thus the dep issues are kept to a small minimum. plus saves time :P

---

### Post by pandoratomorrow on 2007-06-21
I installed tcl 8.4, and it worked great. 

Thanks for the help.

---

