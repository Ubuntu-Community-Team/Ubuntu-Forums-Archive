---
title: "Kubuntu Gutsy Imac g3 slow"
date: 2008-03-10
forum: Apple PPC Users
---

### Post by jrsy85 on 2008-03-10
Hi everyone,

I'm fairly new to linux, but i'm typing on my nc8000 laptop running kubuntu7.10 right now and it is fantastic.

my issue is, i have an old G3 imac 600 that the hard drive died in and i threw a 20gig fireball into. I've installed kubuntu for ppc and it slows right down to freezing at the login page. i have fixed the ide_core module and i do not have dri in my xorg.conf, refresh rates are set right and i have changed the video drivers to the r128 drivers.

can anyone help please i am still stuck, i think xserver is not loading?

thanks,

Joel

---

### Post by stream303 on 2008-03-10
Have you made any additional adjustments to the ati driver settings in xorg more than just changing it to r128?  Sounds like you are on top of it, but just in case here's the link right to the ati/radeon stuff for lurkers...

[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

---

### Post by stream303 on 2008-03-10
Ooops...  Have you tried killing ESD in sound prefs or have problems with the date?  Sounds like you've got this info on hand, but just in case:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-ddd818234162c8eabf09f4c3de25d45dc0209b61](https://wiki.ubuntu.com/PowerPCKnownIssues#head-ddd818234162c8eabf09f4c3de25d45dc0209b61)

---

