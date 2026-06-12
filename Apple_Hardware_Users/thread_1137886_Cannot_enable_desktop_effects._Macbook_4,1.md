---
title: "Cannot enable desktop effects. Macbook 4,1"
date: 2009-04-26
forum: Apple Hardware Users
---

### Post by eric_pwb on 2009-04-26
Hi,

I just finished installing Ubuntu Jaunty 9.04, after installing I am finding out that compiz fusion desktop effects will not enable, but this page [https://help.ubuntu.com/community/MacBook4-1/Jaunty](https://help.ubuntu.com/community/MacBook4-1/Jaunty) states that compiz is supported in Jaunty on Macbook 4,1.

Any suggestions?

Eric

edit: I am using the 64 bit version of Jaunty

---

### Post by Peasantoid on 2009-04-26
Same here on a MacBook3,1. I don't really care though, since I don't use Compiz anyway. Still, I hate to leave things unfixed.

---

### Post by igor_av on 2009-04-26
The GPU is blacklisted. To enable desktop effects, follow those instructions :

[http://soccerislife8.wordpress.com/2008/02/06/how-to-enable-compiz-on-ubuntu-710-if-your-graphics-card-is-blacklisted/]("http://soccerislife8.wordpress.com/2008/02/06/how-to-enable-compiz-on-ubuntu-710-if-your-graphics-card-is-blacklisted/")

---

### Post by eric_pwb on 2009-04-26
> **igor_av said:**
> The GPU is blacklisted. To enable desktop effects, follow those instructions :

[http://soccerislife8.wordpress.com/2008/02/06/how-to-enable-compiz-on-ubuntu-710-if-your-graphics-card-is-blacklisted/]("http://soccerislife8.wordpress.com/2008/02/06/how-to-enable-compiz-on-ubuntu-710-if-your-graphics-card-is-blacklisted/")

Thanks, That did the trick.

Why is the card blacklisted? It worked before

---

### Post by Peasantoid on 2009-04-26
Apparently Compiz doesn't play well with certain rendering methods. Never had a problem myself.

---

### Post by igor_av on 2009-04-26
> **eric_pwb said:**
> Thanks, That did the trick.

Why is the card blacklisted? It worked before

You may have a look at this thread...

[http://ubuntuforums.org/showthread.php?t=701567]("http://ubuntuforums.org/showthread.php?t=701567")

---

