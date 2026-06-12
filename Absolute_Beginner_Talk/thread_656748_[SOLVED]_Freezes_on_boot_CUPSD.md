---
title: "[SOLVED] Freezes on boot CUPSD"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by visionthing on 2008-01-02
Hi
During startup it jumps out of the Ubuntu booting splash screen and goes to terminal showing everything that is loading. It now freezes at the line about Common UNIX Printing SYSTEM CUPSD

Now the only change I have made was to my etc/modules file. Up till this point when everything was fine all it containted was

fuse
lp

I added a line with ndiswrapper to get my wireless working on boot without intervention. This is when the CUPSD error began. I have since removed it from modules and even restored modules file back to only having 

fuse
lp

Even tried with an empty modules file but the error persists. Any ideas? Even a command to remove CUPSD completely from loading. I don't need to print anyway. At least then I could get the OS booting again.

Thanks!

---

### Post by visionthing on 2008-01-02
Sorted it. Booted to Grub. Logged in as root. Did a /etc/init.d/gdm start to launch the GUI. Logged in as myself. Used Synaptic Manager to remove CUPSD components. For the most part that fixed it. ndiswrapper then started troubles but that will be another thread.

---

