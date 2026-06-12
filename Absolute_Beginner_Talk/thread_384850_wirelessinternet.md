---
title: "wireless/internet"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by raymangoose on 2007-03-14
I am very very new to ubuntu. In the interface properties it shows that i am cutching the internet, but when I open the fire fox it gives me following window with error:
terminal
GTK accessibility Module Initialized
(Gecko:5829): Glib-BObject-WARNING**:gsignal.c:1017:unable to lookup signal"activate" of unloaded type 'MaiAtkObject'
(Gecko:5829): Glib-BObject-CRITICAL**:g_signal_emit_valist::assertion 'signal_id>0' failed

---

### Post by seshomaru samma on 2007-03-15
I don't know what does that mean, looks like some sort of bug
Which version of Ubuntu are you using?
Whats the output of this command :
```
dpkg -l |grep firefox
```

anyway , first do :
```
sudo apt-get install opera
```
this will install opera - try to connect to the internet with it 
if you get any errors - post them here

---

