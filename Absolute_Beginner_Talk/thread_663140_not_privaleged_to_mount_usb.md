---
title: "not privaleged to mount usb?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by deezay on 2008-01-09
i upgraded to 7.04 awhile ago, and i guess i have never tried my usb stick. but now when connecting the stick i get the cannot mount error.

i'm assuming this is a quick fix i'm just brain dead at the moment. thanks alot!

---

### Post by RomeReactor on 2008-01-09
Hi. Try going to 'System->Administration->Users & Groups', highlight your account (your username) and press "Properties". There, go to the second tab (User Privileges) and make sure **Access external storage devices automatically** is checked. Then go to 'System->Preferences->Removable Drives and Media' and on the first tab (Storage) make sure the first three boxes are checked.

---

### Post by deezay on 2008-01-09
yup. those were the first things i checked. i can mount/unmount it as root, but not under my username. pretty annoying. would it be something in fstab?

---

### Post by RomeReactor on 2008-01-09
You could try mounting it and do a **cat /etc/fstab**, but that would probably show up as root. Did you chmod, chown or format the USB before? Does this happen in every USB port?

---

### Post by deezay on 2008-01-10
yup. those were the first things i checked. i can mount/unmount it as root, but not under my username. pretty annoying. would it be something in fstab?

---

### Post by deezay on 2008-01-10
sorry about the above post.... don't know what happened there. no i haven't done anything to the usb. and it does it in every port. very confused

---

