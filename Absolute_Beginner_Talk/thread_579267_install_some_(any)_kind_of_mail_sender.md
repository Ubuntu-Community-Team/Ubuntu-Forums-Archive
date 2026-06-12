---
title: "install some (any) kind of mail sender"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-10-18
Hi,

I give up.

I have Ubuntu 7.04 (headless server) installed and I have installed many other daemons and applications.

The most difficult thing I have encountered is getting the damn machine to send an email.

I have no idea about TLS or SASL and I dont have a domain address.

I simply want to use my ISP to route mail generated from my server, using my username and password. I dont want to route mail and I dont (at this stage) want to recieve any mail.

Postfix just refuses to work (cant telnet to port 25) and I just couldnt be bothered any more. Why is this so hard?

Are there simpler options?

dazed and confused.
:confused:

---

### Post by hyper_ch on 2007-10-18
have a look at the perfect howtos written by falko:

[http://www.howtoforge.com](http://www.howtoforge.com)

Simple step-by-step guides that work.

---

### Post by tkharris on 2007-10-18
This is an excellent book for postfix:

[Postfix - The Definitive Guide ( This links to google showing the book )]("http://books.google.com/books?id=YCif7TaRDK0C&dq=Postfix+Books&pg=PP1&ots=yqsmT14x1q&sig=K9TbIOUbJlFV-s1dDNv5LtB1Y6A&prev=http://www.google.com/search%3Fq%3DPostfix%2BBooks%26ie%3Dutf-8%26oe%3Dutf-8%26aq%3Dt%26rls%3Dorg.mozilla:en-US:official%26client%3Dfirefox-a&sa=X&oi=print&ct=result&cd=1&cad=legacy#PPA256,M1")

[http://www.oreilly.com/catalog/postfix/](http://www.oreilly.com/catalog/postfix/)

I highly recommend it.  Email administration is a bit more than "Set it up and see what happens", that's how you end up with open relays.  If you just want to send email through your ISP why don't you install Thunderbird?

---

