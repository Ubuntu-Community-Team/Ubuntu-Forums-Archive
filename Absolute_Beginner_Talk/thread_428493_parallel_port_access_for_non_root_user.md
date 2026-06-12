---
title: "parallel port access for non root user"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by PhilJ on 2007-04-30
Hi all,
 this may be old news and not apply to many but I am still using my old flat bed scanner which is a mustek 600clone  (Funline TS600) which works on parport0 or lpt1 if you prefer.
I have been running gksu xsane to access it until another thread concerning read/write access to a usb printer made me think. I opened my filemanager as root and went to /dev/parport0 and altered the permissions to read write for everyone and also added myself to group lp. Now I can access my scanner without running gksu. This may apply to other devices on this port if like me you are too tight or skint to buy new gear.

Philj

---

### Post by klytu on 2007-05-06
> **PhilJ said:**
> Hi all,
 this may be old news and not apply to many but I am still using my old flat bed scanner which is a mustek 600clone  (Funline TS600) which works on parport0 or lpt1 if you prefer.
I have been running gksu xsane to access it until another thread concerning read/write access to a usb printer made me think. I opened my filemanager as root and went to /dev/parport0 and altered the permissions to read write for everyone and also added myself to group lp. Now I can access my scanner without running gksu. This may apply to other devices on this port if like me you are too tight or skint to buy new gear.

Philj

I use a canon parallel port scanner so this was relevant to me. Your method worked well when I used to run RedHat and Fedora core, but for some reason it didn't work when I first installed Ubuntu Hoary.  I had been invoking xsane with gksudo ever since and  I never bothered trying again changing the permissions on the parallel port as I upgraded to newer versions of Ubuntu. But, yeah it works now! For complete happiness I also had to go into the .sane directory in my home folder and change ownership of it and all subfolders and files  to myself instead of root. Before doing this last change on the .sane directory, whenever I would close xsane  I would get an error message stating "cannot access file: permission denied".

---

