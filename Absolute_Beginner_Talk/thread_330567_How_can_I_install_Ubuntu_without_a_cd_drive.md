---
title: "How can I install Ubuntu without a cd drive?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by rider303 on 2007-01-03
Is it possible to install Ubuntu without a cd-drive? I have the .iso file in my harddisk but I don't have a working cd-drive unfortunately. How can I if possible?

---

### Post by bodhi.zazen on 2007-01-03
See if this helps:

[http://ubuntuforums.org/showthread.php?&t=316093](http://ubuntuforums.org/showthread.php?&t=316093)

[http://doc.gwos.org/index.php/Install_Edgy_6.10_from_an_.iso_file](http://doc.gwos.org/index.php/Install_Edgy_6.10_from_an_.iso_file)

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

---

### Post by bernied on 2007-01-03
1. You could try to put the CD onto a usb stick - but this could be challenging as you will need a different boot method, and you will need to tell the kernel that it's files will be found on the usb stick and not on the cd.

2. You could try a [net install](http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html), using debootstrap

3. You could try a [PXE boot install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

Keep in mind that those two links might refer to very outdated installations of ubuntu, so for instance the apt sources need to be updated, but the methods shouild be similar.

I've done it the second way - it worked with some effort.

---

### Post by bernied on 2007-01-03
That first method from bodhi.zazen's post looks much better than any of mine - I feel like a dinosaur

---

### Post by rider303 on 2007-01-03
Thank you I'll try

---

