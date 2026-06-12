---
title: "GNU on Android?"
date: 2012-04-14
forum: Any Other OS
---

### Post by lolpenguin on 2012-04-14
This is coming out of nowhere, but since much of GNU has been ported to Windows, has anyone thought of porting GNU to Android? Or does it even need porting since Android uses Linux anyway?

---

### Post by sanderd17 on 2012-04-14
There are some "Linux installers" in the market which just install the GNU tools on top of your Android kernel.

Naturally, things like GTK or QT can't be installed, as Android uses a completely different graphcal shell.

---

### Post by roelforg on 2012-04-14
> **sanderd17 said:**
> 
Naturally, things like GTK or QT can't be installed, as Android uses a completely different graphcal shell.
 
Not directly, no...
but if one had the time and interest, one could modify the parts that connect and call X11 and write a little dummy libX11 that takes those calls and forward them to whatever android uses.

---

### Post by lolpenguin on 2012-04-14
> **sanderd17 said:**
> There are some "Linux installers" in the market which just install the GNU tools on top of your Android kernel.

Naturally, things like GTK or QT can't be installed, as Android uses a completely different graphcal shell.

I've seen 'Linux installer' but AFAIK it installs Debian or some other GNOME-based OS, and that's not what I want. Like Ubuntu for Android, that is pretty easy as they share the kernel, but I want GNU with Android, not on top. To clarify, when working in an Android teletype I get quite frustrated that the power of the GNU OS tools isn't there and I have to use some other (crappy) replacement, (e.g. bash, Android only has sh, rm, you can't use the arguments GNU lets you, like -rf).

Of course, Linux installer and Ubuntu for Android are good things, but I'm unlikely to use them because I don't like high-end smartphones with the specs that Ubuntu for Android needs.

---

