---
title: "Ubuntu Server edition - is it what I'm looking for?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by l_tenhunen on 2007-07-29
Hello,

my aim is to setup my old PC as a server for storage purposes. My idea is that my relatives who are scattered around Europe could upload their pictures, videos etc. for viewing. Here are some questions that deeply trouble my mind:

- Do I need a static IP addres from my ISP for this ?
- LAMP installation probably covers my needs, but how do I actually manage my server with it? From terminal, or graphical interface?
- I plan to give everyone a share of the space available, easily done I suppose, but how is uploading done? Not all of my relatives, especially my grandma :mrgreen:, are familiar with terminal or ftp, so graphical interface on server would be nice.
- Is it possible to have somekind of photo gallery program?

---

### Post by meborc on 2007-07-29
the server version of ubuntu does not have a GUI... only terminal (cli)... so you probably need to install some kind of lightweight desktop environment (fluxbox or xfce... etc)

more information here - [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

can't help you with the other stuff.. but wiki is a good place to start looking - wiki.ubuntu.com

---

### Post by armandh on 2007-07-29
services like this solve the ip address problem
[http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)

---

### Post by l_tenhunen on 2007-07-29
Thank you for quick response! I will delve into those links once I get my new harddrive and I'll start to toy around with my project :mrgreen:

---

### Post by Wim Sturkenboom on 2007-07-29
> LAMP installation probably covers my needs, but how do I actually manage my server with it? From terminal, or graphical interface?
You don't manage your server with LAMP. You can learn the CLI, install a leightweight window manager or use webmin.

> Not all of my relatives, especially my grandma are familiar with terminal or ftp, so graphical interface on server would be nice.That will not be a function on the server, You can make a simple web page for the uploads.

> Is it possible to have somekind of photo gallery program?Of course, but I don't know if there are existing ones (do your research). You can always code your own one (or pay me :) ).

---

