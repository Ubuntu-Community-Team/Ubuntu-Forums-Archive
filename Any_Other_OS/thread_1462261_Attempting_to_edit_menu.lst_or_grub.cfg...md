---
title: "Attempting to edit menu.lst or grub.cfg.."
date: 2010-04-25
forum: Any Other OS
---

### Post by subcook on 2010-04-25
Hi,

I am using linux mint 8 - Helena, and am trying to (temporarily) install PloP (the bootloader).

To do this I would normally go into menu.lst and edit it from " /boot/vmlinuz-whatever"  to "/boot/plpinstc.com".  this is how I have to install it.

I noticed these seem to be read-only files so I went and switched permissions but still no luck.

Would anyone be so kind as to point me in the direction of the correct file to edit,  and maybe a recommendation of which line to edit this?

I'm about 2.5 months into linux and love it,  but am new,  please show mercy :-)


thanks in advance guys,


-cheers

---

### Post by oldfred on 2010-04-25
Do not know mint.

Are you now using grub2??

With grub 2 you edit/add entry to 40_custom. Then run sudo update-grub
/etc/grub.d/40_custom

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by subcook on 2010-04-26
This link helped out tremdously,   thanks a bunch,   I dunno why it didn't show up in the google,   but nevertheless,  thank you.



-cheers

---

### Post by gargdada on 2011-04-27
subcook if u successfully installed plop using grub2.. plz guide me through.. i m still unable to do so :-(

---

