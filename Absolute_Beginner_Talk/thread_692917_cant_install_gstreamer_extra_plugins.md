---
title: "cant install gstreamer extra plugins"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-02-10
I double-click a mp3 file.It says :search for suitable codec n stuff.I say ''search''it gives me only gstreamer extra plugins to install.I click it it say confirm installation... i say confirm.It says ''cannot install gstreamer0.10-plugins-ugly cuz the conflicting software must be removed first and says to swithcback to synaptic manager.wadda i do then??

Also, before it told me that my country is not on some list for being able to install it n stuff.Pls help I can't install amarok or VLC and im desperate  listen to sum gud mp3

---

### Post by jan quark on 2008-02-10
hm try to install this

```
sudo apt-get install ubuntu-restricted-extras
```

and in what country do you live if I may ask

---

### Post by munch3 on 2008-02-10
[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras[/PHP]

am from serbia

---

### Post by jan quark on 2008-02-10
hm
are your sources enabled?

check here
system > administration > software sources

check them all except the sources and the CD

the run 

```
sudo apt-get update
```

and try once again to install the restricted extras

---

