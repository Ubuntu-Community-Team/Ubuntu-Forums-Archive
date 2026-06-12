---
title: "Custom SSH"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by sebkinne on 2008-02-25
hello everyone.

Im actually under time preassure, so i really need help.

I need to set up a new user account (yea, i did that)
that can ssh into ONLY a ceartain directory.
eg: /var/www/
i duno how to limit the user to do so.
cos atm, i can ssh into the server, and it looks like the user is root o0
thank you for your help.

sebkinne

---

### Post by wormser on 2008-02-25
That is a great question and something I have thought about setting up.  It looks like you need to use chrooted.  I found a guide [here]("https://wiki.ubuntu.com/DebootstrapChroot").  Keep us up to date on how it goes.  I am going to set it up later.

---

### Post by sebkinne on 2008-02-25
Yea, ill check it out right now.

thank you and ill post again

---

### Post by bodhi.zazen on 2008-02-25
See if these links help at all : 

[http://www.linux.com/feature/61387](http://www.linux.com/feature/61387)

And iron bars, a restricted shell (restricts a user to /home)

Iron Bars : [http://sourceforge.net/projects/ibsh/](http://sourceforge.net/projects/ibsh/)

[http://www.cryptolife.org/2008/02/17/how-to-secure-login-with-linux-restricted-shell/](http://www.cryptolife.org/2008/02/17/how-to-secure-login-with-linux-restricted-shell/)

---

