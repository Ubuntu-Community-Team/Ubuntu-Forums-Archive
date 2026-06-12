---
title: "Synchronising clock to ntp.ubuntulinux.org"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by coolblue on 2005-07-17
Hi
On every bootup, Ubuntu tries to synchronise my clock to ntp.ubuntulinux.org which it ultimately always fails but it all takes such a LOOOOOOOOOOONG TIME that my bootup time gets unnecessarily stretched. Is there any way I can turn off this unnecessary synchronising to make my bootup much faster? 

Plz help.

Thanks a lot.

---

### Post by varunus on 2005-07-17
You can always temporarily hit CTRL-C to skip this process.  (I have to do the same thing when I boot up as I'm not always connected to ethernet).

To turn it off completely, you can always open up a terminal, cd to /etc/init.d/, and use the command "sudo chmod -x ntpdate" to turn it off.  However, that's not the cleanest way; I'm sure someone knows a better one.

---

### Post by rider343 on 2005-07-17
[http://www.ubuntuguide.org/#bum](http://www.ubuntuguide.org/#bum)

---

