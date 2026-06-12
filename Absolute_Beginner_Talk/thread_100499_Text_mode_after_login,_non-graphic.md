---
title: "Text mode after login, non-graphic?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by thunderchase on 2005-12-07
Hi everyone, i'm absolute beginner :( ...

I think i did the installation process fine - i do have some knowledge in software at all. The problem is: every time when booting is done, I would log in, that would pass, and then nothing! Just alphanumeric mode, like unix. My question: how should I start the graphic environment, gnome, and should it be loaded automatically or there's any particular command for that?

Thanks, and sorry for bad english :confused: ...

---

### Post by matthewv on 2005-12-07
It should be loaded automatically. Try running the command "startx" (without quotes) and posting the output here. A ```
sudo dpkg-reconfigure xserver-xorg
```may help..

---

### Post by thunderchase on 2005-12-08
OK, thanks, I'll try that. If it still won't work, i'll have to reinstal ubuntu.

---

### Post by thunderchase on 2005-12-08
I fixed it up. It was me, I screwed up with instalation in the first time :) . Now it's OK.

I have two more questions: is it possible to use my HP Laserjet 1010 and Intel 536EP modem under Ubuntu? How can I mount /dev/hda1 (WinXP) partition and be able to access it with user account?

---

