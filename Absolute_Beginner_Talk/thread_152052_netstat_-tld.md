---
title: "netstat -tld"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-29
I have a few questions about the print-out below.

a) what or who is sunrpc?

b)I thought I had openssh-server on port 22 tcp6 but alas is not there
instead I find these
tcp6       0      0 ip6-localhost:50006     *:*                     LISTEN
tcp6       0      0 *:50009                 *:*                     LISTEN
can any explaination be given please?

lex1;) 

-------------------------------------------------------------------------------------
netstat -tld


Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost.localdo:32770 *:*                     LISTEN
tcp        0      0 localhost.localdo:32771 *:*                     LISTEN
tcp        0      0 *:sunrpc                *:*                     LISTEN
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN
tcp        0      0 *:50008                 *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp6       0      0 ip6-localhost:50006     *:*                     LISTEN
tcp6       0      0 *:50009                 *:*                     LISTEN

---

### Post by bernardfrancois on 2006-03-29
I don't know what it does neither. You can read more with **man netstat** and **info netstat**. I tried to read this stuff quickly, the only thing I found is that option -t stands for TCP and -l stands for listening.

If you find out what *netstat -tld* does exactly, please post it here. I'm curious.

---

