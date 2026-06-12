---
title: "sending data over IP"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by _neda_ on 2008-02-22
Does anybody know an easy way to exchange raw data between two running programs in two computers? 
I'm working on a robotic project and for some reason I'm running the vision program and the control program in two different computers. I'm looking for an easy way to pipe these two program together using a port (like USB) or over IP to exchage simple low size data.I feel there should be an easy way to do that in linux; But after a lot of search about ssh, scp, telnet I'm just more confused.

---

### Post by Cypher on 2008-02-22
All those things you've searched so far as established protocols and programs that use the TCP/IP interface..these aren't used as generic data transfer protocols.

What you need is [Socket Programming]("http://linuxgazette.net/issue74/tougher.html")..use the socket() and accept() functions to establish a connection between two PC's and then you can create your own custom data packet format to transfer between them..

---

