---
title: "cannot mount windows drive(after reseting vista MBR)"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by pcharouz on 2007-10-17
I added ubuntu to the Vista MBR, and now it gives me and error when I try to access my HD.

[[IMG]http://img181.imageshack.us/img181/2760/screenshot2eg2.png[/IMG]](http://imageshack.us)


and this is kind of off topic, but how can I disable my bluetooth modul?

---

### Post by dward526 on 2007-10-18
This is just a theory, but because your boot loader is located in a windows partition, then starts ubuntu, it does not get a chance for a clean shutdown.  On my dual boot machine, if I do not allow windows to shutdown completely, I cannot access the windows drives, just the shared data drive I created later using gparted.  My suggestion is for a dual boot machine, you should install grub.

Hopefully this helps

About bluetooth, I am not sure, sorry.

---

