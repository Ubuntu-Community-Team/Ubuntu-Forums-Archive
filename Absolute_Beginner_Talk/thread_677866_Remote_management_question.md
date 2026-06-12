---
title: "Remote management question"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by jiminizer on 2008-01-25
Hi all 

I would like to remotely my linux server from another PC on the network. At the moment i am trying to build a server that performs a few tasks centered around RADIUS, and if i can get it to work i'll be buying a proper server. At the moment however i have an old PC i can spare, but when i try and boot my HDD with ubuntu on it i get an error that it was unable to start X. on my main PC i can boot just fine, but obviously i need the main PC for other tasks so can't keep using it. 

I was wondering if there was some way i could remotely manage the server and have it booting up in a terminal mode or something so i do not get the X errors, and then have it boot X after somehow? I'm pretty new to linux and not confident enough with the terminal to work on it alone. I currently have the machine configured as an SSH server, and i can use putty to log into it from another PC, however i need a desktop too.

Can anyone help?

Cheers,
Jim

---

### Post by Factory on 2008-01-25
Try installing a server/cli system. Obtain the alternate disk and choose the option "install a cli system". Then try installing xorg from the command line (once you've set up networking the way you want it). After that, if it's an old machine, try installing a light windows manager.

Better explanation: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

If you want remote gui, look into VNC stuff. Once you understand cli well enough, though, you won't need (want) gui, especially for a server rig.

---

