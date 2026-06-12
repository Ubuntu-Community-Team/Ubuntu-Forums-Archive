---
title: "runnning a server on ubunto descktop"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by soviet911 on 2008-02-09
Hi i was woundering if i could host a website of my laptop wich is runnning ubunto 7.10 at the moment, without instaling a dedicated ubunto server since i want to be able to use the laptop for simple things like AIM and useing it as a protable laptop for word processing, the reason i want to make server is to host a website so i could let several of my friends read the book im writing online, So is ther a program i could use to host a website on ubunto 7.10 descktop editinon without installing ubunto server. Thanks. and what program should i use, thanks again.

---

### Post by neurostu on 2008-02-09
A great low resource web server is:

Boa

I have used it a couple times and find it very easy to manage.

```
$sudo apt-get install boa
```

will install it

I would recommend looking at : [http://www.boa.org/documentation/](http://www.boa.org/documentation/)  before you start just so you have an idea of how to set it up properly.

Good luck!

---

### Post by neurostu on 2008-02-09
Sorry i left out, the only thing you really need to do is remember to "bind" boa to your static ip.  Boa will then create a /var/www/ and then anything you place in /var/www/ will visible on a browser!

---

### Post by soviet911 on 2008-02-10
thanks alot i will try that

---

