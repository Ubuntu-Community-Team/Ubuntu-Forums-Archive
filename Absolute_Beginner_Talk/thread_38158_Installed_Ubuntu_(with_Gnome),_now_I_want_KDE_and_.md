---
title: "Installed Ubuntu (with Gnome), now I want KDE and FluxBox as well"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by kentl on 2005-05-30
Hi!

I am very new to linux and especially Ubuntu, but it seems very nice. I installed the Ubuntu image which defaults to having Gnome installed.

I would like to have Gnome, KDE and FluxBox installed at the same time. So that I easily can switch between them until I make up my mind for which one to use.

How would I go about doing this? First I need to install them, and then I need a way to choose which one to use, as Gnome is started automaticly.

If you can point me to a FAQ or similar that's also a great response!

---

### Post by Mez on 2005-05-30
[http://www.ubuntulinux.org/wiki/InstallingKDE](http://www.ubuntulinux.org/wiki/InstallingKDE)

and to install fluxbox

```
sudo apt-get install fluxbox
```

It#'s in universe though, so make sure you have those lines uncommented in your /etc/apt/sources.list

Before you login, there's a "session" button, and there you can choose whether to use Gnome, KDE, fluxbox or whatever ;)

---

### Post by poofyhairguy on 2005-05-30
Fluxbox is pretty hardcore (IMHO). Try KDE first:

sudo apt-get install kubuntu-desktop

---

