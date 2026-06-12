---
title: "configuring ip address problem"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by roy4355 on 2008-02-17
Hi

Totally new to Linux and trying to install ubuntu server version on an old win 2003 server. Seems to install ok, picks up dchp from my router, lets me log on and set a 'root' password, but the problem I can't seem to get past is creating/editing the 'etc/network/interfaces' file to give it a static ip address. Always get the error 'E212: can't open file for writing'. 

I've tried re-installing and doing a 'cat etc/network/interfaces' and it says the file doesn't exist, but I would have thought that once it picked up dchp, then this file would be created - am I wrong?

Logging on as 'root' gives the same error!

I've searched the net for solutions and all I've got for this error is that it is a permissions issue, but surely logging on as 'root' this shouldn't happen.

Any advice would be welcome.

---

### Post by sb12 on 2008-02-17
> **roy4355 said:**
> Hi

Totally new to Linux and trying to install ubuntu server version on an old win 2003 server. Seems to install ok, picks up dchp from my router, lets me log on and set a 'root' password, but the problem I can't seem to get past is creating/editing the 'etc/network/interfaces' file to give it a static ip address. Always get the error 'E212: can't open file for writing'. 

I've tried re-installing and doing a 'cat etc/network/interfaces' and it says the file doesn't exist, but I would have thought that once it picked up dchp, then this file would be created - am I wrong?

Logging on as 'root' gives the same error!

I've searched the net for solutions and all I've got for this error is that it is a permissions issue, but surely logging on as 'root' this shouldn't happen.

Any advice would be welcome.

it would be cat /etc/network/interfaces not cat etc/network/interfaces

---

### Post by roy4355 on 2008-02-17
> **sb12 said:**
> it would be cat /etc/network/interfaces not cat etc/network/interfaces

Hi

Thanks for that, just a case of missing the first '/' on all my commands.

Now 'vi /etc/network/interfaces' has allowed me to edit no problem.

...... Until my next problem.....

Cheers

Roy

---

### Post by talsemgeest on 2008-02-17
Don't forget to mark this thread as solved...

---

