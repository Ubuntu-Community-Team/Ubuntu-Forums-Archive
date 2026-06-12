---
title: "Cant add programs"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by tophue on 2008-02-05
In the add/remove applications window it will not allow me to add any new applications. No matter what I try to add I get a "The list of applications is not available" error, which then says "Click on "reload" to load it. To reload the list you need a working internet connection" I have a working connection (I am posting from it now) and it does load the list of applications, but there is no "reload" button. The error gives me the option of "refresh" or "cancel" and neither seem to do anything. I am on ubuntu 7.10 with a fresh install. anyone know what's up?

---

### Post by jw5801 on 2008-02-05
Try it from the command line:```
sudo apt-get update
```and see what happens. If that returns any errors post the whole output here. You can also install from the command line "sudo apt-get install <package-name>"

---

### Post by tophue on 2008-02-05
this is what I get:

```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Reading package lists... Done

```

Does it think I am not connected or something? I am confused

---

### Post by jan quark on 2008-02-05
please look if you have enabled the sources 

system > administration > software sources

also run this terminal command and post the result

```

cat /etc/apt/sources.list
```

---

### Post by tophue on 2008-02-05
> **jan quark said:**
> please look if you have enabled the sources 

system > administration > software sources

also run this terminal command and post the result

```

cat /etc/apt/sources.list
```

They were't enabled, that fixed it. thanks for the help!

---

### Post by jan quark on 2008-02-05
good to hear

pls mark this thread as solve using the thread tools at the top of the page

thank you

---

