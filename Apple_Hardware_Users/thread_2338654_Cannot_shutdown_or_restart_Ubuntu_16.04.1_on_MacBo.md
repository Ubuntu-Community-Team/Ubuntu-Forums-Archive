---
title: "Cannot shutdown or restart Ubuntu 16.04.1 on MacBook 6,1"
date: 2016-09-30
forum: Apple Hardware Users
---

### Post by kevow on 2016-09-30
I have a white unibody MacBook that I have loaded various flavors of Ubuntu on. It works quite well for the most part, but there is one super annoying issue. It will not fully reboot or shutdown. I have managed to display the terminal messages and there don't appear to be any errors, it just gets to the end of the process and then stops.

Any ideas how I can troubleshoot this further or fix this issue? TIA

---

### Post by kevow on 2016-09-30
So I found an old thread about this and the solution was to add reboot=pci to the options in grubs config file.

[https://help.ubuntu.com/community/Grub2#Fixing_reboot.2Fshutdown_freezes](https://help.ubuntu.com/community/Grub2#Fixing_reboot.2Fshutdown_freezes)

---

