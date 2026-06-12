---
title: "Gutsy x86 in VMWare Fusion on Santa Rosa Macbook: Display problem"
date: 2007-12-04
forum: Apple Intel Users
---

### Post by stoned_ninja on 2007-12-04
I've performed a default installation of Gutsy x86 (no tweaking whatsoever) inside VMWare Fusion 1.1. The only thing I had to change was the display resolution within the live environment, since it selected a resolution higher than the Macbook's 1280x800. Everything went flawlessly.

Upon rebooting the VM, I found it impossible to login. Gutsy resizes the VMWare window a few times (testing for suitable resolutions), gets to the login screen and freezes. I cannot see the username text field at all because much of the screen is black. I also cannot get to the console with C-M-F1 or restart X with C-M-Backspace.

Has anybody else experienced this issue? Is there a way I can boot it in console mode?



EDIT: I solved this by installing VMWare Tools after booting the VM. Now I just have to figure out how to get wireless working.

---

