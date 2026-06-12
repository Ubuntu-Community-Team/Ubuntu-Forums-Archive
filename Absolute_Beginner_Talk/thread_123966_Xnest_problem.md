---
title: "Xnest problem"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by PatrickMay16 on 2006-01-31
Hello.

I've been trying to use Xnest by using this command: 
> 
Xnest :1

And it seems to work OK, however there's a problem. When I try to do "xterm -display :1", I get this error:
> 
patrick@ubuntu:~$ xterm -display :1
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

xterm Xt error: Can't open display: :1

And in the terminal I started Xnest in, this appears:
> 
AUDIT: Tue Jan 31 17:08:11 2006: 24390 Xnest: client 1 rejected from local host


It seems like it's rejecting it for some reason. I read through the man page for Xnest and I didn't find anything that helped. Does anyone know what to do?

I'd really appreciate any help.

---

### Post by PatrickMay16 on 2006-01-31
Ah, never mind. Seems like you just need to use the option "-ac" to disable access control restrictions.

---

