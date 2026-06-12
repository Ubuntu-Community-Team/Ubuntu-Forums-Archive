---
title: "AMSN Upgrade"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by peakshysteria on 2007-12-29
Can anyone tell me how to upgrade to the latest stable AMSN-0.97 and keeping my settings, plugins and skins!?

Can i just install it over the current one by making the amsn-0.97-1.tcl84.x86.package executable? Or do i have to uninstall the current version?

Better to ask first since i'm kinda new to Ubuntu :)

---

### Post by K.Mandla on 2007-12-30
Moved to Absolute Beginner Talk.

---

### Post by Martje_001 on 2007-12-30
1) Download this: [http://surfnet.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.tar.bz2](http://surfnet.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.tar.bz2)
2) Unpack it somewhere
3) Open a terminal
4) typ: **cd /the/directory/where/you/unpacked/amsn**
5) typ: **sudo apt-get install tcl8.4-dev tk8.4-dev**
6) typ: **./configure**

If no errors:

7)** typ: make**
8)** typ: sudo make install**

After that you can delete the directory where you unpacked amsn. Hope this helps.

Edit: Never install things with 'autopackage'. It really sucks ;)

---

### Post by Welcomed Rain on 2008-01-08
I ran into a problem following your instructions. The first part went without a hitch (no errors) but when I went to complete the last two commands, I ran into a problem with the very first, i.e. "typ: make"

The response I received was "make: *** No targets specified and no makefile found.  Stop." What have I done wrong?

Thanks!
Welcomed Rain

---

### Post by capink on 2008-01-09
There are precompiled package of the latest stable amsn [here]("http://ubuntuforums.org/showthread.php?t=649364&highlight=amsn").

Your settings are stored on your home directory. So they will not be overwirtten by the new package.

Skins are stored in /usr/share/amsn/skins. They will only be deleted if they were part of the old packgage (not manually copied by you) in which case you can back up using:

```
[CODE]sudo cd -av /usr/share/amsn/skins/* /back/up/location
```[/CODE]

---

### Post by Welcomed Rain on 2008-01-09
Thanks for your help! 

Welcomed Rain

---

