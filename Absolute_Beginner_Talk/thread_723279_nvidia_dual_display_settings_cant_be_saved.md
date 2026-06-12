---
title: "nvidia dual display settings cant be saved"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by robalcorn on 2008-03-13
Hey folks. I recently installed Ubuntu 7.10 and love it. Just having a few issues most I have solved with goggle but this one has me stumped. I am using a nvidia 6200 pcie card with a gateway 1540 lcd and a acer al1912 lcd. I have the restricted drivers installed and with the option under system/administration/screens and graphics I can have a mirrored default screen. My goal is to have the acer work to the right and the gateway to be the primary ie so I can surf the web on one screen and watch tv on the other. So I used the alt-f2 function for the run command and typed nvidia-settings which comes up but when I try to save the settings I get this message : Unable to create new X config backup file '/etc/X11/xorg.conf.backup'. Any suggestions to get around this?

---

### Post by reeseslover531 on 2008-03-13
When nvidia settings is run as the local user it doesnt have the rights to edit the xorg file.  Run sudo nvidia-settings from the terminal and change what you need, saving should work with that.

---

### Post by robalcorn on 2008-03-13
Thanks reeseslover531 that solved the problem. I could have sworn I tried that but apparently not lol. Anyways thanks so much now I am a happy camper.

---

### Post by bodhi.zazen on 2008-03-13
> **reeseslover531 said:**
> When nvidia settings is run as the local user it doesnt have the rights to edit the xorg file.  Run sudo nvidia-settings from the terminal and change what you need, saving should work with that.

Consider advising gksu (kdesu with KDE) for graphical apps.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

