---
title: "Trying to install modem drivers and configure"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Midgetprawn on 2008-02-25
Good morrow fellow vegetables
Having installed Ubuntu 7.10 onto my Elonex computer I have tried to et it up and running online using the internal PCtel Mdc modem. I tracked down the appropriate drivers using scan modem only to find that I needed a smartlink driver which said I had to install packages sl-modem.*
One of these is on the GutsyGibbon disc the other I had to download. How do I install a [COLOR="Red"]package [/COLOR]which is a [COLOR="red"]tarball [/COLOR]on a [COLOR="red"]memory stick [/COLOR]onto a laptop which cannot connect to the internet

---

### Post by renzokuken on 2008-02-25
firstly, a tarball is a compressed archive, much like a .zip or .rar file. first extract it somewhere, then inspect the contents and look for a README or INSTALL file that should explain how.

if it is source code (which it most likely is) you will need to compile it yourself, which in order to do successfully, you also need to have the **build-essential** package......which i'm not sure how to install without a net connection.

---

