---
title: "Visual effect ??"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by jbalazs on 2008-02-21
When I try to activate visual effects in ubuntu 7.10 I get this warning how can I get a round it ???

[IMG]http://i5.photobucket.com/albums/y176/foxhunter2/Screenshot.png[/IMG]

---

### Post by jbalazs on 2008-02-21
anybody ??

---

### Post by TeoBigusGeekus on 2008-02-21
Have you enabled+downloaded the restricted graphic card driver for your system?

---

### Post by jan quark on 2008-02-21
first what is your graphic card?

second do you have installed the drivers?

---

### Post by jbalazs on 2008-02-21
ATI graphic card, how to enable+download the restricted graphic card driver ??

---

### Post by jan quark on 2008-02-21
go to system > administration > restricted driver manager
and check the box to activate the drivers


you will also probably will have to install this

```
sudo apt-get install xserver-xgl
```

and select xclient session during the login

---

### Post by Sceiron on 2008-02-21
Type in terminal
```
glxinfo
```
paste the output here.

---

