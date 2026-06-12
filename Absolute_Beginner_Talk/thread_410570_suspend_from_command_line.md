---
title: "suspend from command line"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by nosh on 2007-04-15
very quick question: how do I send my laptop into suspend mode directly from the command line?

---

### Post by speeves on 2007-04-15
In a not very intuitive manner, you can send your laptop into hibernation by using the following command:

dbus-send --session --dest=org.gnome.PowerManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/PowerManager org.gnome.PowerManager.Hibernate

I would put that in a shell script in /usr/local/bin/mysuspend:
#!/bin/sh

dbus-send --session --dest=org.gnome.PowerManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/PowerManager org.gnome.PowerManager.Hibernate

Then chmod it to:

chmod 755 /usr/local/bin/mysuspend

You could then run "mysuspend" from anywhere, and execute the same command above...  I found this at:
[http://live.gnome.org/GnomePowerManager/FAQ#head-ca9ddd6e2954f42fa6fb45b392ece499a6f8ab6f](http://live.gnome.org/GnomePowerManager/FAQ#head-ca9ddd6e2954f42fa6fb45b392ece499a6f8ab6f)

---

### Post by speeves on 2007-04-15
To Suspend to RAM, you just change the final word:

dbus-send --session --dest=org.gnome.PowerManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/PowerManager org.gnome.PowerManager.Suspend

---

### Post by nosh on 2007-04-15
sweet, it is kind of convoluted, but thank you very much!

---

### Post by nosh on 2007-04-15
oh, hang on...
I'm sorry.  I forgot to mention that I'm running xubuntu, and it looks like that is an internal command for gnome, right?

anyone know how to do it for xfce?

---

### Post by FuturePast on 2007-05-13
if you still need to do this, it's ~$ sudo /etc/acpi/sleep.sh sleep
or (to get to the nitty gritty) sudo echo -n S3 >/sys/power/state

---

### Post by deragon on 2008-04-16
For posterity, here is an updated version to suspend to ram with newer version of Gnome (Ubuntu 08.04 Hardy Heron).  To hibernate, simply replace "Suspend" with "Hibernate".

dbus-send \
  --session \
  --dest=org.freedesktop.PowerManagement \
  --type=method_call \
  --print-reply \
  --reply-timeout=2000 \
  /org/freedesktop/PowerManagement \
  org.freedesktop.PowerManagement.Suspend

---

