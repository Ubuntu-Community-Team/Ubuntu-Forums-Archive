---
title: "Unable to install NVidia driver"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by PZJM on 2008-01-18
Hey folks, I finally installed Ubuntu 7.10.  However, when I try and switch my background from None to Normal I am told that "The software source for the package nvidia-glx-new is not enabled".

My question is how to enable this or even load a up-to-date driver?

My MOBO has an onboard graphics card - Biostar GeoForce 6100-M7, socket 754.  Any help would be greatly appreciated.  Thanks...

---

### Post by cecure on 2008-01-18
Take a look at this guide [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver")
cheers

---

### Post by Digger78 on 2008-01-18
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by RomeReactor on 2008-01-18
Hi. PZJM, if your performed Ubuntu's installation without an internet connection, your software sources are disabled by the system; to enable them, open Software Sources (System->Administration->Software Sources), on the first tab (Ubuntu Software) check the first four cases except for 'Sources' and 'CD-ROM'. You'll be prompted to reload the repository information, and after that, go to 'System->Administration->Restricted Drivers Manager' and enable the drivers for your card there.

---

### Post by PZJM on 2008-01-18
Fantastic.  I will try this when I get home from work.  Thanks for the suggestions and I'll post back what the results were...

---

