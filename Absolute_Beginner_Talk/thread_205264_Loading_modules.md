---
title: "Loading modules"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by gregorycroes on 2006-06-28
Hallo,
I had been trying to load a module. (Gkrellm-i8k) I tried it sudo modprobe i8k force =1 and it went ok. Now I am trying to make it load automaticly. What i did read over internet is that i can do it via adding a ''usbcore'' in directory /etc/modules to load "usbcore.ko" module. I try but no result i couldn't be able so save changes in modules, either vi nor  kate. Could someone know how to do it? I hope some one does.

Regards,
gregory

---

### Post by digby on 2006-06-28
In order to actually edit /etc/modules, you need to be root since root owns that file.  You can do this with```
sudo vi /etc/modules
or
sudo gedit /etc/modules
```
or insert your favorite editor.

---

### Post by Apple 101 on 2006-06-28
I prefer *gedit* for GUI work, and *pico* for command line work.  Did */etc/modules* replace the */etc/modules.conf* (or *conf.modules*) runtime file?

---

