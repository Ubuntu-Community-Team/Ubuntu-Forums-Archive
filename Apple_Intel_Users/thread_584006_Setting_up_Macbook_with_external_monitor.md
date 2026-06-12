---
title: "Setting up Macbook with external monitor"
date: 2007-10-20
forum: Apple Intel Users
---

### Post by schauerlich on 2007-10-20
I have a 1680x1050 Proview 2200W monitor plugged into a 2nd gen Macbook running Gutsy, and I want to set it so the external is the main display and use the Macbook for an extended desktop. The best I can get so far is the Macbook to mirror the external, but it only shows the upper left 1280x800 pixels, and when I try to maximize anything, it'll only bring it up to that size on the external. Can anyone help?

---

### Post by schauerlich on 2007-10-21
Bumping...

---

### Post by cyberdork33 on 2007-10-21
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

### Post by schauerlich on 2007-10-21
I honestly don't understand that... I'm really new.

---

### Post by Tavis on 2007-10-23
I can't get it to work at all.  I'm running a new Macbook (core duo, not pro), and when I go to Sytem->Administration->Screens and graphics and switch the default rate to screen 2 (and then restart X), gdm fails to load.  The splash screen and the console are both visible on the external monitor, just not X.  I'm using an XVGA projector, and I've tried 640x480, 800x600, and 1024x768 to no avail.  

Also, the options to use it as a secondary screen or mirror the default screen are greyed out.  Any suggestions?

Thanks,
Tavis

---

### Post by Tavis on 2007-10-23
I can't get it to work at all.  I'm running Gutsy on a new Macbook (core duo, not pro), and when I go to Sytem->Administration->Screens and graphics and switch the default rate to screen 2 (and then restart X), gdm fails to load.  The splash screen and the console are both visible on the external monitor, just not X.  I'm using an XVGA projector, and I've tried 640x480, 800x600, and 1024x768 to no avail.  

Also, the options to use it as a secondary screen or mirror the default screen are greyed out.  Any suggestions?

Thanks,
Tavis

---

### Post by cyberdork33 on 2007-10-23
See the Release Notes for Gutsy:
[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

---

