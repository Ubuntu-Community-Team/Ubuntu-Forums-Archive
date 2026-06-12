---
title: "help with terminal: ?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by bryan1ari on 2008-02-14
Hi! everyone, I am new to the Linux with the Ubuntu platform.  I hope everyone is as helpful as I was told.  This my not be a problem for some of you but it is a real pain for me, as I am still just learning of this system way.   I got tired of MS saying I performed an illegal whatever.  Anyway, glad I am through with that now.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bryan1ari@bryan1ari:~$ I didn't know what to input for these two lines.  any suggestions would be greatly appreciated.  thanks  David

---

### Post by taurus on 2008-02-14
Make sure you close synaptic, Add/Remove, or adept before you run any apt-get/aptitude from a terminal.

---

### Post by bryan1ari on 2008-02-14
Could you please be a little more helpful and explain what you mean in laymans terms.  I don't know the terms add/remove or adept, or how to use them.  thanks and please don't get irritated with me. For asking...:)

---

### Post by emarkd on 2008-02-14
You'll find this is a friendly place.  After all, who else should we expect in the beginner's forum besides beginners ;)

The package system keeps up with all the installed software on your Ubuntu, so it can only do one thing at a time.  If you run the Add/Remove Programs or Synaptic (System > Administration), then you can't run apt-get from the command line without closing the other first.  The lock error you got above is because you've got two different installers going at once.

---

### Post by LowSky on 2008-02-14
what tuarus was saying was dont have another programs or windows open while trying out commands.

Add/Remove is a program that can automatically fetch programs and install them for you
you can find it under the Applications menu

Synaptic is also a program that can fetch and install programs and is alot more extensive than Add/Remove it is located under System> Administration>Synaptic

Apt-get/aptitude is a command that you can tyoe in the Terminal (like DOS) that is used to fetch programs and install programs as long as you know its name and the program is availible. Synaptic is the graphical version of apt-get.

hope this makes sense... enjoy linux

---

### Post by bryan1ari on 2008-02-15
Thank you for clarifying this problem for me.  I will read on and learn to use the installer programs and synaptics package installers, thanks again.

---

### Post by erginemr on 2008-02-15
> **bryan1ari said:**
> Thank you for clarifying this problem for me.  I will read on and learn to use the installer programs and synaptics package installers, thanks again.

Welcome to the Ubuntu Forum and Linux in general. Now that you are willing to learn the ins and outs of Ubuntu/Linux, I'd like to suggest a few easy to follow tutorials:

1. Ubuntu Desktop Guide: 
[https://help.ubuntu.com/ubuntu/desktopguide/en_GB/](https://help.ubuntu.com/ubuntu/desktopguide/en_GB/)

2. Tuxfiles: (command line tutorial)
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

3. How to install ANYTHING in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Hope you will enjoy your new system as much as we all do.

Take Care.

---

### Post by jan quark on 2008-02-15
welcome bryan1ari

there are no stupid questions
you can ask whatever you want

the links above-mentioned are good
you have to know linux is different than the other OSs out there, and much better:)

there is of course a phase when you are like : Where am I ?

but everybody had this feeling once

just now I am making an Virtual Ubuntu Tour, 
two pages are finished, and many more will come
I plan to add many pics and videos, so the advantages of Ubuntu will be stresses and emphasised in  the best possible way

so check out my site(signature) and click to Ubuntu tour

---

