---
title: "connect to mysql host using host computer name rather than ip address"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Ba66e77 on 2007-06-10
Full disclosure: I know jack about networking and not much about MySQL administration.

I have things set up so that my laptop can connect to my the MySQL server running on my desktop, if I use the ip address of the desktop.  What I'd like is to use the host-name of the desktop, though.

$> mysql -h desktop -p
ERROR 2005 (HY000): Unknown MySQL server host 'desktop' (1)

Doing the same thing using the host's ip address works.

Can someone give me a pointer on how to set that up?  I don't even know the terminology which would let me get a good search running. 

Thanks

---

### Post by ThinkBuntu on 2007-06-10
Couldn't you just use a symlink with your desired name, linking to the IP? Never linked a server to the desktop myself, but just an idea.

---

