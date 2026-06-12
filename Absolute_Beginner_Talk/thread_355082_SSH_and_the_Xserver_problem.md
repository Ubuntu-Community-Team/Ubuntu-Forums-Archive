---
title: "SSH and the Xserver problem"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by g3k0 on 2007-02-06
When I SSH into my schools server and try to run a program with gui I get this error 
[bwhit132@csunix ~]$ kcalc &
[1] 18733
[bwhit132@csunix ~]$ kcalc: cannot connect to X server

I am using Edgy.  This worked previously in Dapper.  What do I need to change to get this to work.

---

### Post by ^rooker on 2007-02-06
- Check your environmental variable $DISPLAY. 
If I remember correctly it should be something like: "0.0"

- Additionally, see if X11-forwarding is enabled by the server/client (/etc/ssh/sshd.conf).

---

### Post by g3k0 on 2007-02-06
Hmmm still no go... Not really sure what Im looking for iin the file though.  I uncommented the x11 ones and changed them to yes though.

---

### Post by ^rooker on 2007-02-06
what do you see after executing "echo $DISPLAY" while being logged in at your school's server?

---

### Post by g3k0 on 2007-02-06
Well initially nothing, but I did an export DISPLAY=localhost:0.0

---

### Post by g3k0 on 2007-02-06
Anyone know what to do?  I really need this to work.

---

### Post by g3k0 on 2007-02-06
ack help!  :confused:

---

### Post by g3k0 on 2007-02-06
I am retarded I figured out what I was doing.
I was typing ssh -x -l user server
the X is supposed to be capital!   lol hahhahahaaaaaaaa sorry for my stupidity and wasting peoples time

---

