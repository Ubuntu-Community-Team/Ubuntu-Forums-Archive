---
title: "Mysql question"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by jpoblocki on 2008-03-09
I hope this is in the right forum.  I am a COMPLETE LINUX NEWB.  I am trying to setup mysql on my sever computer which is in chicago at my sisters house and I live in wisconsin, how can i set it up so that I can access mysql from outside her house i have tried for almost two weeks now, wading thru page after page after page of commands to no avail.  Is there someone who can help out this "special" newb linux user *LOL*

---

### Post by Peter09 on 2008-03-09
Well you can enable remote support like this :-

[http://ubuntuforums.org/showthread.php?t=299489](http://ubuntuforums.org/showthread.php?t=299489)

you can then connect to your sisters machine and remotely manage it.

PC

---

### Post by Peter09 on 2008-03-09
Just to confirm,
on her machine issue 

x11vnc -noxdamage -connect <your IP address>

on your machine issue

vncviewer -listen

---

### Post by jpoblocki on 2008-03-09
wouldnt the server in chicage be the one set to listen?

---

### Post by jpoblocki on 2008-03-09
I also have Gutsy Gibbon installed on that machine which that says it will not work with Gutsy Gibbon

---

### Post by Peter09 on 2008-03-09
No, yours is set to listen, your sister makes a request to your machine. Its more secure in a way because her request is directed straight to your machine. Also she does not have to open her firewall, although you do, but then I guess you know more about Linux than she does.

As for not working, I have it working between two gustsy machines. The addition is to put the switch -noxdamage in the command line. This gets over the problem.

PC

---

### Post by krunge on 2008-03-09
> **Peter09 said:**
> Just to confirm, on her machine issue 

x11vnc -noxdamage -connect <your IP address>

on your machine issue

vncviewer -listen

Be sure to run these in the opposite order.  I.e. you must run the 'vncviewer -listen' before the 'x11vnc -connect ...' is run.

---

