---
title: "installing wine"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Irti on 2007-06-02
how do i go abt installing wine...cant find it in synaptics package manager....................

---

### Post by Crafty Kisses on 2007-06-02
Download a program called "AutoMatix"
[http://getautomatix.com]("http://getautomatix.com")
Go to "system tools" and check the box that says "Wine" and press install.

---

### Post by jonward0690 on 2007-06-02
Just type in "sudo apt-get install wine"

---

### Post by Simran on 2007-06-02
If you have automatix installed you can use that to install wine. [www.getautomatix.com](www.getautomatix.com) if not [www.winehq.com](www.winehq.com) all the info is there

Simran

---

### Post by daschmidty on 2007-06-02
or if you just enable the universe and multiverse repositories, you should be able to apt-get it.

```
sudo vim /etc/apt/sources.list
```
and then uncomment all of the lines starting with deb and deb-src

---

### Post by bodhi.zazen on 2007-06-02
Installing automatix just to then install wine seems well a little like buying an 18 wheel truck to carry your groceries home.

Linux has a long tradition of KISS ~ Keep It Simple Stuipd

Adding repositories is very very simple : [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then use Synaptic to search and install wine.

It is the post-install stuff that well get you. Wine is not a simple program to use :

[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by AndyCooll on 2007-06-02
As the last post says System > Administration > Synaptic Package Manager

Under Settings > Repositories add Universe and Multiverse. Then do a "Reload".

Finally do a search for Wine, and voila!

:cool:

---

### Post by Irti on 2007-06-02
thanx ppl......am starting to finally gt sumwhere now:D

---

