---
title: "Hardy Heron Alpha 4 PowerBook G4 Works"
date: 2008-02-09
forum: Apple PPC Users
---

### Post by xevix on 2008-02-09
Just wanted to announce that I upgraded from Gutsy to Hardy alpha 4 and it's working as well as Gutsy.  I just did what it said to do here: [http://akso.wordpress.com/2008/02/04/upgrade-ubuntu-gutsy-to-hardy-alpha-4/](http://akso.wordpress.com/2008/02/04/upgrade-ubuntu-gutsy-to-hardy-alpha-4/)

One problem you might run into is openoffice package collisions, but just follow the on-screen instructions ordering you to do "apt-get install -f" and whatnot repeatedly, and you should be fine.  Keep trying to dist-upgrade until it works =p

---

### Post by stream303 on 2008-02-10
Allright!

Were you able to load any images from the internal cd rom, or did you have to use an external unit like I did on my G5 iMac?

---

### Post by xevix on 2008-02-10
I upgraded using apt-get, didn't do a fresh new install so no need for a cdrom drive at all.

---

### Post by soar on 2008-02-12
By chance, are you using Leopard? I mean- as a primary OS?
And if no, were you using it when you installed your first version of Ubuntu?

---

### Post by stmiller on 2008-02-16
I'm testing Hardy on my 867Mhz G4 Tibook. There is a huge bug where sleep/suspend does not occur. (It is not even an option in the power menu.) Also sound is still broken on tibooks, though there is a patch on launchpad for that snd-powermac bug report.

Here is the suspend bug report that has a script workaround: [https://bugs.launchpad.net/ubuntu/+bug/144305](https://bugs.launchpad.net/ubuntu/+bug/144305)

---

