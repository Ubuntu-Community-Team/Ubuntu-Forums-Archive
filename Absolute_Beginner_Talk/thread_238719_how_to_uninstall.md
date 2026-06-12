---
title: "how to uninstall?"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by zasdarq on 2006-08-18
Sorry if this is a stupid question, but there are a couple programs that I've installed (tovid and advmame)  that I would like to remove.  Advmame was installed using...

./configure
make
make install

So it's not in the synaptic package or the applications list... how do I remove it?

Thanks!

Matthew

---

### Post by Perfect Storm on 2006-08-18
Do this from from the folder which you compiled the application:

```
sudo make uninstall
```

When compiling try use 
```
sudo checkinstall
```
Though not all applications can use it. But this command makes a fake .deb which make it easy to uninstall etc.

To get it
```
sudo apt-get install checkinstall
```

---

### Post by Freakenstein on 2006-08-18
You could also use **sudo apt-get remove advmame**.

---

