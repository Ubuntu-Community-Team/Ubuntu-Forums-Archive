---
title: "my Ubuntu isnt giving me a display"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Alashagra on 2006-12-02
I installed ubuntu recently on my computer. But when i  start it up it goes through the loading screen but then it gives out and it cant display any visual.

---

### Post by zytsef on 2006-12-02
Sounds like a driver thing. Try booting to the comand line by putting in the installation cd and selecting recovery mode. Then post the output for the command 'lspci -v'. Also, mount your root partition (should be something like 'mnt /dev/hda1') 'cd' to /<mountpoint>/etc/X11/, copy the monitor and graphics device sections and post them here.

This will give us a starting point for the kind of information needed to troubleshoot this.

---

