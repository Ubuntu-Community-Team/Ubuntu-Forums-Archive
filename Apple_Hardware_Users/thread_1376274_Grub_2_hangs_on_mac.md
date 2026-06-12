---
title: "Grub 2 hangs on mac"
date: 2010-01-09
forum: Apple Hardware Users
---

### Post by romejoe on 2010-01-09
I have a macbook pro 5,3 and I have it triple booting osx, ubuntu 9.10 and windows 7. recently when I tried to load ubuntu and windows grub would hang. I don't get any error messages or the "Grub Loading" message all I get is "Grub _" printed on the  screen and nothing happens no matter how long i leave it. I can get ubuntu and 7 to load by using the super grub disk and booting that way. I have also tried to reinstall grub and Ubuntu completely. Any ideas how to fix it?

---

### Post by linuxopjemac on 2010-01-09
I would boot from a liveCd and go into a console and try to reinstall Grub2

sudo grub-install /dev/sda

(in case sda is your hard disk)

I would also sync the partition table after this from within rEFIt.

---

### Post by romejoe on 2010-01-09
ok that worked thank you

---

