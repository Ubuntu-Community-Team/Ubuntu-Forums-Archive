---
title: "My Compaq Presario V2000 always wants to boot from network"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-03-15
It is pretty weird.  Whenever I leave an ethernet cable connected to my lappy it will not boot up by itself unless I press the "escape" button to stop it trying to boot from the network. If I wander away after turning it on and forget about it grub gets all messed up. Is there a simple way to disable booting from the network?

---

### Post by Mogurijin on 2008-03-15
Go into BIOS and check your boot order. You will need to hit a button to go into BIOS on boot up. Look around while your booting to look for a message like "Hit this button to enter BIOS (sometimes setup)".

It might help if we had your manufacturer so we know what BIOS we are dealing with.

---

### Post by 1875 on 2008-03-15
Have you got PXE set as your first boot device in your BIOS ? If so set your HDD as your first boot device.

---

