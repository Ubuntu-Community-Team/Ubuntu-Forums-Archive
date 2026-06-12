---
title: "OSX in VMware"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by dacool25 on 2007-04-02
Okay, so i've successfully installed osx in vmware, but now i just have a few bugs and was wondering if anyone knew how to fix them.

1.  I can't connect to the internet, as of right now i have a bridged connection, but i don't know what to change it to or how to get the Internet to work 

2.  I have scroll bars (since i can't get full screen) on the right and bottom of the screen.  Does anyone know how to set it for the guest os to automatically fit the screen?

Thanks

EDIT: okay, i solved problem number two by editing the vmware preferences file and changed a few things around.  But now i can't connect to the internet.  Right now when i type ifconfig (in ubuntu) i have the following: eth0, lo, vmnet1, vmnet8, and wlan0.  But my problem is that the virtual machine is using the vmnet to connect to the internet, and i believe that you need vmware tools for this to work.  Does anyone have ANY ideas?!

---

### Post by Locutus_of_Borg on 2008-07-12
I am in the same situation.

What did you do to get the screen to auto-fit?

My XP guest can connect to the internet, but OS X cannot, both using NAT.

---

### Post by Locutus_of_Borg on 2008-07-12
I now have internet, but still no autofit

---

