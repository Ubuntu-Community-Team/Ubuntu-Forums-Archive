---
title: "installing programmes"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by smile-its-smiley on 2006-06-29
how do i install programmes this have really baffled me, i was trying to intstall amsn and a few other programmes and i just cant work out how to do it

---

### Post by Jagot on 2006-06-29
aMSN is in the universe repository, which you will need to activate.  You can find out how to do that here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then in Synaptic (System, Admin) you will be able to search for amsn and you can install from there, or from Terminal (Applications, Accessories) you can do this:

```
sudo aptitude update && sudo aptitude install amsn
```

You can find out more about installing applications here:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by taurus on 2006-06-29
It depends what format you are talking about.  The easiest way is to use apt-get/aptitude/synaptic.  Otherwise, download a .deb and install it with dpkg.  Or else download the source and build from it!!!
```

sudo apt-get install <program name>
-or-
sudo dpkg -i <filename>.deb

```

---

### Post by smile-its-smiley on 2006-06-29
how do i install a .tar file and .gz

---

### Post by Jagot on 2006-06-29
[QUOTE=smile-its-smiley]how do i install a .tar file and .gz[/QUOTE]

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by smile-its-smiley on 2006-06-29
that is very complicated for a ubuntu newbie could you give me a step by step guide

---

### Post by aysiu on 2006-06-29
[QUOTE=smile-its-smiley]that is very complicated for a ubuntu newbie could you give me a step by step guide[/QUOTE]
I don't think you're going to get any more step-by-step than the Monkeyblog tutorial.

You can try this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

