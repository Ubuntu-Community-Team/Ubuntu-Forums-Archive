---
title: "network stopped working"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-08-22
Hi,

I have been using a Broadband connection very successfully( Sify Broadband) since the day I started using Ubuntu ( 3 months now). I could connect till one hour back.

However it is not connecting now. The output of the command to connect is as under:

> Checking reachability of Sify Server...                                         : Success
Checking whether instance sifyclient already running....            : NO
Establishing sify broadband connection...Segmentation fault   ( core dumped)

Can any tell me what is this segmentation fault and core dumped?
It is running nicely in XP.
Do I need to do any changes to my settings?
Thanks.
Going bonkers without network in Ubuntu.

---

### Post by kidcharles on 2007-08-22
Out of curiosity, what program are you running that outputs those messages? It looks like something called 'sifyclient'. Is that necessary to connect?

---

### Post by gupta_sumesh63 on 2007-08-22
Yes. Thats the internet service provider, thats Sify Broadband. They provide a connection client called sifyclient to connect to their servers. It was working fine till now. However now it says segmentation fault. What could be the probable reason?

---

### Post by kidcharles on 2007-08-22
A segmentation fault is a very low-level, basic error that can occur, it is a problem with memory.

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

You may have to contact your broadband provider to figure out what the problem might be. (This is why I greatly prefer connections that don't require proprietary clients.)

---

