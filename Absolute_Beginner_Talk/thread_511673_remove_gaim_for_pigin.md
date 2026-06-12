---
title: "remove gaim for pigin"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-07-28
how can i remove gaim because i want to install pigin

---

### Post by felicity on 2007-07-28
I'm not sure how to remove it as I think it's attached to ubuntu-desktop or something, but you can always install pidgin anyway and manually remove gaim from your main menu.

---

### Post by tomcheng76 on 2007-07-28
download your pidgin [here]("http://www.getdeb.net/app.php?name=Pidgin")
```

sudo apt-get remove gaim ubuntu-desktop
sudo dpkg -i <yourpidginfilename>
sudo apt-get install ubuntu-desktop

```

---

### Post by llzero1337 on 2007-07-28
sudo dpkg -i pidgin_2.0.0-1_i386.deb
dpkg: error processing pidgin_2.0.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 pidgin_2.0.0-1_i386.deb

---

### Post by llzero1337 on 2007-07-28
ok tis

---

### Post by Solidad on 2007-07-28
is pigin compatible to dapper drake?

---

### Post by Bachstelze on 2007-07-28
There is no Pidgin package in the official Dapper reposiories but a quick Google search will give you lots of third-party repos that have some.

---

### Post by tomcheng76 on 2007-07-28
u see something like this
Download:   pidgin  (1.8 Mb)  ,  pidgin-data  (6.1 Mb)
plz download both of them
then
```

sudo dpkg -i pidgin*.deb

```

---

### Post by por100pre1 on 2007-07-28
> **felicity said:**
> I'm not sure how to remove it as I think it's attached to ubuntu-desktop or something, but you can always install pidgin anyway and manually remove gaim from your main menu.

You can remove ubuntu-desktop, it's only a checklist of the packages of the default Ubuntu installation, it's nothing to worry about. :)

---

### Post by orbital on 2007-07-29
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libavahi-compat-howl0 (>= 0.6.0); however:
  Package libavahi-compat-howl0 is not installed.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin

Having trouble installing Pidgin from the .deb. Please help!

---

### Post by AlexenderReez on 2007-07-29
> **orbital said:**
> dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libavahi-compat-howl0 (>= 0.6.0); however:
  Package libavahi-compat-howl0 is not installed.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin

Having trouble installing Pidgin from the .deb. Please help!

please install pidgin from extra repo....or using deb package installer ...it will handle dependencies for you :)..double click pidgin-data ,then double click pidgin ..it is really dangerous to use dpkg unless you are sure you have installed all dependencies...but it is worthless ,just use deb package installer and not waste your time to check the dependencies :)

---

### Post by orbital on 2007-07-29
> **AlexenderReez said:**
> please install pidgin from extra repo....or using deb package installer ...it will handle dependencies for you :)..double click pidgin-data ,then double click pidgin ..it is really dangerous to use dpkg unless you are sure you have installed all dependencies...but it is worthless ,just use deb package installer and not waste your time to check the dependencies :)

What lines do I need to add to sources.list for the extra repo?

---

### Post by atomkarinca on 2007-07-29
i used this link to install pidgin: [http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/](http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/)

and you can remove gaim with no worries.

---

### Post by orbital on 2007-07-30
> **atomkarinca said:**
> i used this link to install pidgin: [http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/](http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/)

and you can remove gaim with no worries.

Thanks this worked.

---

