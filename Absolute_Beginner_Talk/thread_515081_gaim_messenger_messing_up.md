---
title: "gaim messenger messing up"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-08-01
hello,

i've been using ubuntu for quite a few months, and gaim has been working perfectly fine with me.
recently i bought a new computer and set up gaim as my gmail chat/google talk client. it worked ok the first few times. since yesterday, whenever i start it up it shows me a blank screen and status as connecting and it never loads the list of contacts. it stays like that forever and does it every time i try to restart it.

has anyone had this happened to them? any idea what went wrong and how to fix it?
any help appreciated.

thank you.

---

### Post by bulldog060 on 2007-08-01
switch to pidgin ( the replacement for gaim ) ... i was having alot of trouble with gaim connecting to google as well but since i switched i haven't had any problems.

~ron

---

### Post by obbe on 2007-08-01
maybe it's just a server issue otherwise try updating gaim to pidgin

---

### Post by shadowboxer_k on 2007-08-01
thanks, ron :)

that's exactly what i am trying to do now, following the instructions [here.]("http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/") 
i seem to be doing something wrong at the ./configure make sudo make install step though, because it gives me a weird error like this:

```
kris@kris-desktop:~$ cd pidgin-2.0.1./configure
bash: cd: pidgin-2.0.1./configure: No such file or directory
kris@kris-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
kris@kris-desktop:~$ sudo make install./configure

```

any idea what to do?
sorry i'm changing the topic of the thread. 

thanks

---

### Post by bulldog060 on 2007-08-01
> **shadowboxer_k said:**
> thanks, ron :)

that's exactly what i am trying to do now, following the instructions [here.]("http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/") 
i seem to be doing something wrong at the ./configure make sudo make install step though, because it gives me a weird error like this:

```
kris@kris-desktop:~$ cd pidgin-2.0.1./configure
bash: cd: pidgin-2.0.1./configure: No such file or directory
kris@kris-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
kris@kris-desktop:~$ sudo make install./configure

```

any idea what to do?
sorry i'm changing the topic of the thread. 

thanks

your missing a return on that first line:
**$ cd pidgin-2.0.1./configure**

try it this way 

[B]$sudo -s
$ cd pidgin-2.0.1
$ ./configure
$ make && make install [/B]

without that return it thinks that is one long directory name

---

### Post by shadowboxer_k on 2007-08-01
thank you! that worked :)

---

### Post by shadowboxer_k on 2007-08-01
it worked, i managed to install it, but the same thing happens as with gaim.

i try to start it up and all it shows is an empty window. it doesn't even give me the option to set it up correctly. :(

i wonder what's gone wrong.

---

### Post by shadowboxer_k on 2007-08-01
strangely, after a restart, it began to work. :)
this seems to be becoming a pattern with me, hehe. thanks for all the help!

---

