---
title: "Triple boot method"
date: 2007-11-14
forum: Apple Intel Users
---

### Post by Aemelica on 2007-11-14
There was a method a while ago for triple booting that did now involve editing the lilo.conf file. I believe it involved installing grub on the ubunto partition instead of on the boot partition and it used reffit as the bootloader. 

Is this method still kicking around? I can't seem to find it.

---

### Post by pxwpxw on 2007-11-14
[http://ubuntuforums.org/showthread.php?t=594298](http://ubuntuforums.org/showthread.php?t=594298)

---

### Post by cyberdork33 on 2007-11-14
> **Aemelica said:**
> There was a method a while ago for triple booting that did now involve editing the lilo.conf file. I believe it involved installing grub on the ubunto partition instead of on the boot partition and it used reffit as the bootloader. 

Is this method still kicking around? I can't seem to find it.
All you have to do is install rEFIt in OSX, and make sure to specify during the installation to install grub to the Ubuntu partition instead of the MBR. See link in my sig.

---

