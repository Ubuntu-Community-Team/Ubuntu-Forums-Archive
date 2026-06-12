---
title: "How to configre x NOT to autostart"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by sbaker33 on 2005-06-27
How can I configure the X-server **not ** to autostart when booting?  I want to boot to the commandline and only start X when I type startx.
Thanks
-sbaker

---

### Post by wylfing on 2005-06-27
I believe Ubuntu's default runlevel is 2. Therefore, you could go into /etc/rc2.d and rename 'S13gdm' to 'X13gdm' to stop it from running when runlevel 2 is launched. That should do it for you, and it's easily reversed if you change your mind later.

One more thing: if you ever upgrade the gdm package, it will write a new link into /etc/rc2.d, thus starting X automatically again. Just watch for gdm upgrades, and afterwards go clean house in /etc/rc2.d to keep things running the way to you like.

---

