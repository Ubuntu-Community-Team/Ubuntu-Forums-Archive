---
title: "Uninstalling programs... Especially Pypanel"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by fobnicat on 2007-04-12
How do I uninstall programs like Pypanel.. ever since I installed it i ahve had a few issues and being that it doesnt work anyways.. might as well uninstall it.. I'm a complete newb at this so if there is a tutuorial that I missed, that woudl be great.. THanks!

---

### Post by mac.ryan on 2007-04-12
System -> Administration -> Synaptics
then click on the ckeckbox and select "mark for removal"
then click on "apply"

---

### Post by fobnicat on 2007-04-12
if for some reason it is not in the Synaptics?

---

### Post by mac.ryan on 2007-04-12
It depends how you installed it. How did you? (please give link to the how-to or detailed explanation)

---

### Post by fobnicat on 2007-04-12
I installed it through terminal, cant find the link to where i was told to install it that way...

but once i installed it i followed these directions to try to fix it....

[http://ubuntuforums.org/showthread.php?t=327514](http://ubuntuforums.org/showthread.php?t=327514)

---

### Post by mac.ryan on 2007-04-12
From terminal, you might have done either apt-get, aptitude, used a bin file or having compiled the sources, so it is difficult to give you directions... :(

you might try to issue the following command and see if any of these work:

```
sudo apt-get remove pypanel
``````
sudo aptitude purge pypanel
```

---

### Post by fobnicat on 2007-04-12
thanks a ton! i'll let you know how it goes...

---

