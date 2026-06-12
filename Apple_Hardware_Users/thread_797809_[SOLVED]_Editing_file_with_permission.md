---
title: "[SOLVED] Editing file with permission"
date: 2008-05-17
forum: Apple Hardware Users
---

### Post by Officer Dibble on 2008-05-17
At the below link are instructions to get the sound working in Ubuntu on a MacBook.

[http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/](http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/)

It says that I am to add a line to the options file - when I do and I try to save it I am told I don't have permission - how do I do this, please? Typically when I need to do something as root I am asked for my password, but it isn't doing this for some reason.

Many thanks for any advice. :)

---

### Post by frog_pilot on 2008-05-17
you have to open this options file with an editor with root privileges to apply changes to it

usually (with installed gui) ```
sudo gedit /file/you/want/to/edit
```

In your case open a terminal, execute ```
sudo gedit /etc/modprobe.d/options
``` add your line, save+exit

and you're done

---

### Post by Officer Dibble on 2008-05-18
Splendid, many thanks. :)

---

