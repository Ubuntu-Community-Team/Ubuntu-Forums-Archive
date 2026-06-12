---
title: "Old imac needs desktop &amp; software for kids"
date: 2008-05-25
forum: Apple Hardware Users
---

### Post by john_spiral on 2008-05-25
Hi,

I [[COLOR="Blue"]freecycled[/COLOR]]("http://www.freecycle.org/") an old imac to a family down the road, who intend using the machine for their young kids.

Any recommendations on desktop environment/software, is it possible to get edubuntu software working without too much trouble?

thanks in advance

John

---

### Post by frog_pilot on 2008-05-25
[https://wiki.ubuntu.com/PowerPC](https://wiki.ubuntu.com/PowerPC)

---

### Post by Phonan on 2008-05-25
If you want to install Edubuntu, your best bet is to first install Ubuntu. The livecd is available at [http://cdimage.ubuntu.com/ports/releases/8.04/release/ubuntu-8.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/8.04/release/ubuntu-8.04-desktop-powerpc.iso)

Then you can use the Edubuntu cd to add the educational software: [http://cdimage.ubuntu.com/ports/releases/8.04/release/ubuntu-8.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/8.04/release/ubuntu-8.04-desktop-powerpc.iso)

Or you can simply open a terminal and type "sudo apt-get install edubuntu-desktop-addon"

One last way is to download the server install
[http://cdimage.ubuntu.com/ubuntu-server/ports/daily/current/hardy-server-powerpc.iso](http://cdimage.ubuntu.com/ubuntu-server/ports/daily/current/hardy-server-powerpc.iso)
 and burn that to a cd. After using the text-based installer and booting to a full system, just type "sudo apt-get install edubuntu-desktop"

By the way, if anyone on the forums sees that this is wrong, please let me know- this is how it works as best I can figure out.

Edubuntu, though, may not be the best choice depending on the computer's specifications. Xubuntu is good for systems with less resources, and since this is an old computer, Xubuntu may be the way to go.

---

