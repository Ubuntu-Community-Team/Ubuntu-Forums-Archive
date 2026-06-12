---
title: "Server/Desktop Versions"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Sig_ZA on 2007-06-09
I'm a linux noob and I'm thinking of changing my disto to Ubuntu from Mandrivia.

The PC will need to function as a server (web, proxy, file etc.) and as a desktop.

Can I install both the server and desktop versions on to the PC as one installation.

And also how easier is it to configure the server software? Is there a GUI or is everything done through editing config files and using the console?

---

### Post by ikonia on 2007-06-09
just install the desktop version - you can load things like squid, iptables, apache etc on the destop version fine, and will meet your requirments.

---

### Post by darkfame on 2007-06-09
If you install the server edition, you're installing a stripped down version of Ubuntu with only the necessary tools to host server applications (apache, php, sql etc.). This means there will be no graphical interface by default. If you want, you can install x.org and a lightweight desktop manager like xfce4. By installing the desktop edition you will sacrifice some resources to services and applications not needed on a server.

---

### Post by Sig_ZA on 2007-06-09
That "one-click" LAMP installation offered with the server versions looks like something I would like to try.
Will I still be able to install the server stuff this wayif I install the desktop version?

---

### Post by darkfame on 2007-06-09
> **Sig_ZA said:**
> Will I still be able to install the server stuff this wayif I install the desktop version?

Yes, they both use the same repository.

---

