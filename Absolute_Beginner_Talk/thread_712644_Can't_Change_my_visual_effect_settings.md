---
title: "Can't Change my visual effect settings?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2008-03-01
I've just re-installed Ubuntu 7.10 again however this time using Wubi.
However I cannot seem to change my Appearence Prefrences>Visual Effect Settings

I just get a:
The Composite extension is not available
every time I try.

Any help?

---

### Post by overdrank on 2008-03-01
> **SamTyson92 said:**
> I've just re-installed Ubuntu 7.10 again however this time using Wubi.
However I cannot seem to change my Appearence Prefrences>Visual Effect Settings

I just get a:
The Composite extension is not available
every time I try.

Any help?

HI and have you installed the drivers for you graphics card and what is the model?

---

### Post by SamTyson92 on 2008-03-02
> **overdrank said:**
> HI and have you installed the drivers for you graphics card and what is the model?

I have a ATI Radeon Xpress 200M, I have installed the restricted drivers but its not working.

---

### Post by northern lights on 2008-03-02
[https://answers.launchpad.net/ubuntu/+question/12823]("https://answers.launchpad.net/ubuntu/+question/12823")
[https://answers.launchpad.net/ubuntu/+faq/17]("https://answers.launchpad.net/ubuntu/+faq/17")

---

### Post by jan quark on 2008-03-02
this worked for me:

install this package via terminal

```
sudo apt-get install xserver-xgl
```

and change the session during the login to xclient

---

