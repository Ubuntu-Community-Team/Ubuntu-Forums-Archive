---
title: "Gutenprint?"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Bizmac on 2006-10-08
Hello,

I try to install my printer (CX4800). The scanner is ok with Sane and some conf modification, but when I add the printer and follow the KDE printer setting wizard there is a message error (I try also with the administrator mode):

> Unable to load the requested driver:
Unable to create the Foomatic driver [Epson-Stylus_CX4800,gutenprint]. Either that driver does not exist, or you don't have the required permissions to perform that operation.

I googled and found that Gutenprint is not available on Sourceforge!!!
Maybe I am doing something wrong??? :-k Am I the only one to try to use gutenprint or Foomatic driver?

---

### Post by DarkN00b on 2006-10-08
Open Synaptic package manager and search for gutenprint, It is in there. If it is already installed, you might try removing it with Synaptic and then reinstalling it.

---

### Post by Bizmac on 2006-10-09
Good job DarkNOOb!

I just reinstall the CUPs drivers with gutenprint...and now my printer was perfectly recognized and installed with Kubuntu...

Thank you!

---

### Post by DarkN00b on 2006-10-09
You are welcome. I was *finally* able to actually help someone. Kinda gives you a warm fuzzy feeling. :-D

---

### Post by zibi on 2007-02-23
I don't find a package named gutenprint : the only gutenprint packages I find are: gutenbrowser,  guten-doc and gutenprint-locales.

I have the libgutenprint2 and the libgutenprintui2-1 packages installed as well as the cupsys-driver-gutenrpint one.

Maybe I have already the driver installed, but i doubt it is so:  my printer (lexmark optra e+) is terribly    slow and in [www.openprinting.org](www.openprinting.org) they suggest that the gutenprint driver solves this problem.

HOw can I know which drivers are installed?
In case, which package should I install to get the gutenprint  driver?

I hope to have made myself coprehensible.

---

