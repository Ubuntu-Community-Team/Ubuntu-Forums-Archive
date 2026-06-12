---
title: "Update manager problems"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by gacostac on 2007-10-07
Hi

I get the following error when trying tu run update manager:


'E:Type '“deb' is not known on line 34 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

I get the same one when running apt-get in the terminal. 
Can anyone help me fix it?

---

### Post by rsambuca on 2007-10-07
You have an error on the 34th line of your sources.list.  You can edit the file with this command```
gksudo gedit /etc/apt/sources.list
```If you do not know what to change, then just copy your sources.list here and we can tell you how to fix it.

---

### Post by gacostac on 2007-10-07
Thanks Rsambuka
Dad did it, I had some junk written there that I have no idea how it got there. It was very obvious so i just deleted it and it works now. Thanks

---

