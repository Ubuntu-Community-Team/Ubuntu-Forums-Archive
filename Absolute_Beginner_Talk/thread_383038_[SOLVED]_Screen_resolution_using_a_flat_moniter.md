---
title: "[SOLVED] Screen resolution using a flat moniter"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-12
Ok, im using Ubuntu 6.10, the screen resolution is 1024x768 the height seems to be ok, just the width isnt right.. im using a Packard bell flat-screen wich only allows auto adjust and doesnt seem to fix the problem, is there a way i can manually adjust the resolution?

Thanks, Davey

---

### Post by Dr. Nick on 2007-03-12
You can directly edit the file

/etc/X11/xorg.conf to add resolutions. Is it a wide screen monitor or a standard one?

Also is it stretched or just go off the screen?

---

### Post by DaveyG on 2007-03-12
Thanks for your help.

> Is it a wide screen monitor or a standard one?

standard

> Also is it stretched or just go off the screen?

Neither, just a bit too thin.

---

### Post by Dr. Nick on 2007-03-12
OK, the reason I asked is because most monitors allow you to manually stretch or shrink the image size if you look around in the monitors menu.

If you try to edit the xorg.file be sure to back it up and adjust the resolution in the correct color depth section.

---

