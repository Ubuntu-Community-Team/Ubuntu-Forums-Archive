---
title: "[SOLVED] Gutsy Ndiswrapper freeze?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Onay on 2007-10-19
So I got the latest ndiswrapper (1.48 source code and I compiled it in my new Gutsy installation, and the drivers installed fine. I load the module to the kernel, and everything is going smoothly. Now, though, when I try to connect to my wireless router (encrypted with WEP-64 bit) which worked fine in Fiesty, the network manager attempts to connect for a second or two, then the entire desktop freezes. Mouse doesn't work and I can't even restart X.

Is this an Ndiswrapper problem, a Network Manager problem, or a Dbus problem? Or could it be something else?

I have tried a make uninstall and make distclean before recompiling and the same problem keeps occuring. I'm afraid that if I save my aliases with ndiswrapper -m then the system won't boot up at all. Anybody got any idea?

By the way I'm in my old Fiesty installation now so if you ask me to test certain things it might take me some time to reply, since I'd have to reboot to try it. Thanks everyone.

---

### Post by Onay on 2007-10-19
Bump

---

### Post by Onay on 2007-10-19
Okay I tried it once and it didn't freeze, but it could not connect with a WEP Key! I am positive that the key is right and with the right settings to it, so I'm not sure what the problem is...

---

### Post by Onay on 2007-10-19
Bump...

I can't believe this took a step back... uggh. Fiesty for another 6 months...

---

### Post by Onay on 2007-10-19
See ya later Gutsy.

---

### Post by Onay on 2007-10-20
SOLVED!

The big problem: Ndiswrapper-1.48 does not work with gutsy and my drivers. I recommend anyone using ndiswrapper to get 1.47 (utils and common v1.9).

---

### Post by gamx on 2007-10-20
I am so glad to see your posts! This is exactly my problem. When I connect wireless and a wep key is required the computer freezes. Everything!
Moreover, if I ask network manager to show me the available networks, it says that all networks are at 0% signal. After I connect (to one that does not have protection, of course) the signal keeps on changing in crazy ways, and eventually it freezes.
My version of ndiswrapper is 1.45, the one that comes with Gutsy... My card is a linksys.
Please help!

---

### Post by Onay on 2007-10-20
Try using version 1.47, it worked well for me in feisty and works like a charm in Gutsy as well. I posted a tutorial on how to do this for a DWL-G132 wireless adapter, but I'm guessing that you can just replace the .inf files in the tutorial with your own.

Good luck.

---

