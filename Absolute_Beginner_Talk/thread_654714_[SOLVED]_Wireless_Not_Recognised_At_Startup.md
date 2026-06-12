---
title: "[SOLVED] Wireless Not Recognised At Startup"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by tim237 on 2007-12-31
Hi guys

I'm running Ubuntu 7.10 on a laptop with a INPROCOMM IPN 2220 Wireless LAN Adapter. My wireless works if I go to terminal and type in "modprobe ndiswrapper", but every start up I have to enter this into the terminal again.

Any ideas how I can solve this problem? If you need any more info feel free to ask.

P.S. Absolute newbie, I don't even know what "modprobe" means, I just copied it off someone's post and it worked!

---

### Post by Vadi on 2007-12-31
I get this problem too, but in the development version of ubuntu ("hardy").

modprobe basically loads the ndiswrapper module into the kernel. It should be loading the module automatically at startup though!

If anyone knows how to solve this, please post.

---

### Post by p_quarles on 2007-12-31
You can add that module to the startup sequence this way:
```
sudo sh -c "echo 'ndiswrapper' >> /etc/modules"
```
Be *very* careful to make sure you enter two ">"s in that command -- using one will overwrite the file. If that worries you, you can also simply edit the file manually.

---

