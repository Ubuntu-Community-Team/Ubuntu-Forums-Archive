---
title: "[SOLVED] Proxy conflict between Gnome and Synaptic"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by mysticmatrix on 2007-08-16
I am behind a HTTP proxy requiring authentication.
I am having a proxy setting conflict between Synaptic and Gnome proxy.

With Gnome proxy set through System --> Preferences --> Network Proxy; I can get my cover art in Rythmbox, apt-get in terminal, and all other things except using Synaptic to install new packages. Synaptic keeps on complaing about Internet connection.

To use Synaptic, I must set proxy in Synaptic and disable proxy in Network Proxy.

Is there a way I can use both together?

---

### Post by mysticmatrix on 2007-08-16
*Bump*

---

### Post by soliac on 2007-09-05
Try this:

Setup the System>Preferences>Network Proxy.

Then press Alt-F2 and type: gksu gedit /etc/apt/apt.conf
Put this line in, replacing parts with your actual details:
Acquire::http::Proxy "http://username:password@proxyaddress:port";

Save, and start up Synaptic to see if it works.

---

### Post by mysticmatrix on 2007-09-11
> **soliac said:**
> Try this:

Setup the System>Preferences>Network Proxy.

Then press Alt-F2 and type: gksu gedit /etc/apt/apt.conf
Put this line in, replacing parts with your actual details:
Acquire::http::Proxy "http://username:password@proxyaddress:port";

Save, and start up Synaptic to see if it works.

No, this doesn't seems to do the trick. The only difference I notice is that it doesn't matter anymore whether I give Synaptic a proxy, or tell it direct connection.
The conflict between Synaptic and Gnome proxy exist.

---

### Post by mysticmatrix on 2007-09-27
Fixed in Gutsy :) :guitar: :guitar:

---

