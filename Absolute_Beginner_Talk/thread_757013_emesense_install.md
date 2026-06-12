---
title: "emesense install"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by epicmono on 2008-04-16
i downloaded the emesense deb files archive file and extracted on my desktop...
the folder size is 1.3 mb
i'm using ubuntu 6.06 LTS

how do i install it ??

and also what are the netwrok configurations that i have to make in gaim messenger ?? i just cant seem to log in with gaim kmess and also aMSN.... i'm using broadband.. my pc is connected in a lan with the service provider... :|

---

### Post by meborc on 2008-04-17
from emesene wiki:

> **Manual installation**

Download the .tar.gz, extract and run:

tar xvzf emesene*.tar.gz
cd emesene*
./emesene
[B]
[SIZE="6"]OR[/SIZE][/B]

**APT repository**

Add emesene source:

sudo gedit /etc/apt/sources.list

Paste this at the bottom of the file :

deb [http://apt.emesene.org/](http://apt.emesene.org/) ./
deb-src [http://apt.emesene.org/](http://apt.emesene.org/) ./

Install emesene:

sudo apt-get update
sudo apt-get install emesene


i would go with the apt repo install, cuz then you will get updates as new emesene versions are released

---

