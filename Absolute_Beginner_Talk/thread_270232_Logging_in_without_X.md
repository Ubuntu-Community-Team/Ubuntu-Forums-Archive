---
title: "Logging in without X"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-02
Hey guys,
"Logging in without X?" in other words logging in through the terminal
Very simple question and I'm hoping it is also a SIMPLE answer such as pressing a key when booting. Thanks.

Edit: by the way, I only want to do this one time for now. Thanks.

---

### Post by era86 on 2006-10-02
Well.. a one time solution for what? Just wondering.

The way I do this is I get sysv-rc-conf from the repository and disable gdm. That way I login through the terminal and hit startx to boot up my gui.

Lemme know if that somewhat answers your question.

era

---

### Post by Dual Cortex on 2006-10-02
Wanted to install the nvidia 8774 drivers.
I've almost messed up the xorg.conf before from another method. Now I just want to try out nvidia's method.
HOw to I access sysv-rc-conf and disable gdm?

---

### Post by jaboua on 2006-10-02
If it is just for one time like installing nvidia drivers, you might as well do this:
sudo /etc/init.d/gdm stop

That will not prevent GDM from autostarting at boot, but it will stop GDM for now. To start GDM again, run:
sudo /etc/init.d/gdm start

---

### Post by Dual Cortex on 2006-10-02
> **jaboua said:**
> If it is just for one time like installing nvidia drivers, you might as well do this:
sudo /etc/init.d/gdm stop

That will not prevent GDM from autostarting at boot, but it will stop GDM for now. To start GDM again, run:
sudo /etc/init.d/gdm start

Thanks, I believe this is just what I needed. I'll have to try it out tomorrow since my parents made  me "go to sleep."
I'm writing this through my PSP... and it's a pain in the a...

---

