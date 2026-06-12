---
title: "clamav refuses to die"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-08-01
clamav is COMPLETELY uninstalled on my machine, but when i restart x using the ctrl>>alt>>backspace key combo, it says something about it not finding the proper clamav init file...  how do i get rid of that?

---

### Post by milosz.galazka on 2007-08-02
Hello, 

Maybe it used init script which you can find in /etc/ directory and then rc0.d/ to rc5.d/ and init.d/.
There should be a message left in /var/log/messages

---

### Post by Raineer on 2007-08-02
It could also be mentioned in /etc/rc.local  file, or check in "Sessions" from the GNOME menu and see if it's trying to start there.

---

### Post by asmoore82 on 2007-08-02
ctrl+alt+bs is not "restarting;" it's **killing**

---

### Post by Niklas Schröder on 2007-08-02
sorry about that.  ^_^;  i started this thread at three in the morning.  :p

edit: and i know it's not restarting.  i just prefer it to actually restarting.  yes, yes.  i know it doesn't do exactly the same thing, but that's not exactly why i started this thread is it?  :p

---

