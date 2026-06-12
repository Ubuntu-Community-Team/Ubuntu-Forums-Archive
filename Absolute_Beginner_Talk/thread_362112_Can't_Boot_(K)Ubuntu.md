---
title: "Can't Boot (K)Ubuntu"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-02-15
I accidentally installed kubuntu-desktop. Now, when I try to boot, I get the kubuntu splash screen, and then I'm dumped to  a terminal showing the --bind and --move examples of mount (probably it's man page). I can't enter anything here. Ctrl+Alt+Fx don't work either. Is there any way I can fix this? I can't boot into any other kernel/recovery mode in grub either. I can boot a live cd (don't know if this can help.

---

### Post by highneko on 2007-02-15
I don't know what chroot is or if it would help. If it is what I think it is then maybe you could use it to change your root directory after mounting the root partition then uninstall kubuntu-desktop using a livecd?

---

### Post by nhandler on 2007-02-15
> **highneko said:**
> I don't know what chroot is or if it would help. If it is what I think it is then maybe you could use it to change your root directory after mounting the root partition then uninstall kubuntu-desktop using a livecd?

Would that work? I thought apt-get and aptitude always used the apps on the current computer (in this case, the live cd).

---

