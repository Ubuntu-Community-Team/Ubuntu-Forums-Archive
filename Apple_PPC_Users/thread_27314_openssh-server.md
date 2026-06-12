---
title: "openssh-server"
date: 2005-04-15
forum: Apple PPC Users
---

### Post by poopdeville on 2005-04-15
Hi everybody,

I'm having a bit of trouble getting openssh installed on my fresh hoary ppc installation.  I ran "sudo apt-get install openssh-server" just fine, but the daemon didn't work.  After a while, I decided to try removing it and re-installing.  When I did this, debconf said something about me having to edit my PAM settings.  I've tried doing that, but I've only become lost.

Little help?

---

### Post by accuser on 2005-04-15
Don't know if this helps, but I did:
```
$ atp-get install ssh
```
And everything worked ok. I think that openssh-server is a dependency of ssh, so it is likely that you don't have everything you need installed. Try the above and it may solve your problem.

---

### Post by stensen on 2005-04-27
[QUOTE=accuser]Don't know if this helps, but I did:
```
$ atp-get install ssh
```
And everything worked ok. I think that openssh-server is a dependency of ssh, so it is likely that you don't have everything you need installed. Try the above and it may solve your problem.[/QUOTE]


you have to write apt-get install shh
and not (atp)

:-)

---

### Post by bugmenot on 2005-08-21
[QUOTE=stensen]you have to write apt-get install shh
and not (atp)

:-)[/QUOTE]



And Stensen... you might try:

apt-get install ssh and not shh


hheehe...

---

