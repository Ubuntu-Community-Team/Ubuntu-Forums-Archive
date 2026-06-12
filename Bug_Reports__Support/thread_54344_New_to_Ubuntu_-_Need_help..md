---
title: "New to Ubuntu - Need help."
date: 2005-08-04
forum: Bug Reports / Support
---

### Post by Kareem on 2005-08-04
Hello all! I installed Ubunto (5.04) on my laptop yesterday. It's my first time using an operating system other than MS.

Anyways, I think it is obvious that i'm running through some problems. For one, i know nothing about Linux and Ubuntu. I was hoping if i get some links to some good tutorials or books. The real problem however is that i don't know how to configure my ethernet on Linux (i'm still using XP  :-| ). In device manager, i see that the network cards are identified, but when i press Network, the window doesn't appear. 

Is there any information i should give so that i can get proper help?

---

### Post by charlieg on 2005-08-04
Well, since Ubuntu is Debian-based, the official Debian docs are always handy:
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)

Of course, there's always TLDP ([Linux Documentation Project](http://www.tldp.org)) with it's howto:
[http://www.tldp.org/HOWTO/NET3-4-HOWTO.html](http://www.tldp.org/HOWTO/NET3-4-HOWTO.html)

It also has an overview of networking on Linux:
[http://www.tldp.org/HOWTO/Networking-Overview-HOWTO.html](http://www.tldp.org/HOWTO/Networking-Overview-HOWTO.html)

Also, if you feel a little adventurous, you can just go with the raw docs - 'man':
```
$ man ifconfig
```

I hope that's a good starting point.  If not, there's always [Google](http://www.google.co.uk/search?q=network+config+debian&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)!

---

### Post by charlieg on 2005-08-05
Also if you can give the output of 'ifconfig', that'd be handy.

---

### Post by Kareem on 2005-08-06
There are some programmes that i can't run. I click on them, the processor works, but they never open. One of them is the Root Terminal. I'll make a list of what's not working, and post it in a while. Thanks for all the help so far.

---

