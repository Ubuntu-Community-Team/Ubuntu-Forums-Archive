---
title: "anyone know how to add a sudoer"
date: 2008-05-09
forum: BSD
---

### Post by swoll1980 on 2008-05-09
can't figure it out man visudo isn't helping either

---

### Post by cardinals_fan on 2008-05-09
> **swoll1980 said:**
> can't figure it out man visudo isn't helping either
[http://www.gratisoft.us/sudo/man/visudo.html](http://www.gratisoft.us/sudo/man/visudo.html)

What doesn't work?

EDIT: You might want to look at this... [http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by swoll1980 on 2008-05-09
this is what I got from typing man visudo in the terminal. It doesn't really tell how to add a sudoer. Maybe I'm dumb or something :confused:

---

### Post by cardinals_fan on 2008-05-09
It's odd, which is why I never bother.  Just use su.  If you need sudo, check this out: [http://www.onlamp.com/pub/a/bsd/2002/08/29/Big_Scary_Daemons.html?page=1](http://www.onlamp.com/pub/a/bsd/2002/08/29/Big_Scary_Daemons.html?page=1)

---

### Post by Xappe on 2008-05-09
if you want the user to get full sudo rights, just add the username to the admin group.
<edit> sorry didn't realize you did not discuss ubuntu </edit>

---

### Post by MONODA on 2008-05-10
you need to install sudo, it isnt installed by default. Try launching sysinstall and install sudo from there, I think you should be able to do it that way. If not, try uswing the normal package managemnt system

---

### Post by swoll1980 on 2008-05-10
> **MONODA said:**
> you need to install sudo, it isnt installed by default. Try launching sysinstall and install sudo from there, I think you should be able to do it that way. If not, try uswing the normal package managemnt system

I got it installed. The problem I'm having is that I can't figure out how to add sudoers to the file. su is a pain because I can't open apps with it. 
like if I try to open konquerer it will give me a 'can't open screen error'

---

### Post by LLS on 2008-05-10
```
man sudoers 5
``` explains some about users and user-groups etc.

---

### Post by cardinals_fan on 2008-05-10
> **swoll1980 said:**
> I got it installed. The problem I'm having is that I can't figure out how to add sudoers to the file. su is a pain because I can't open apps with it. 
like if I try to open konquerer it will give me a 'can't open screen error'
Did you read this: [http://www.onlamp.com/pub/a/bsd/2002/08/29/Big_Scary_Daemons.html?page=1](http://www.onlamp.com/pub/a/bsd/2002/08/29/Big_Scary_Daemons.html?page=1) ?

---

### Post by MONODA on 2008-05-11
this may help you: [http://wiki.archlinux.org/index.php/Sudo](http://wiki.archlinux.org/index.php/Sudo)

---

### Post by swoll1980 on 2008-05-11
> **cardinals_fan said:**
> Did you read this: [http://www.onlamp.com/pub/a/bsd/2002/08/29/Big_Scary_Daemons.html?page=1](http://www.onlamp.com/pub/a/bsd/2002/08/29/Big_Scary_Daemons.html?page=1) ?

I got it now. Thanks!

---

### Post by cardinals_fan on 2008-05-11
> **swoll1980 said:**
> I got it now. Thanks!
No problem.

---

