---
title: "help with editing in textmode"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-03-26
does anybody know if i can edit my /etc/X11/xorg.conf from text mode. i changed my driver from ati to radeon and now i can only start in text mode. i want to change back to ati but i dont know the commands to get to and edit the /etc/X11/xorg.conf
i am working from a live cd now maybe i can edit the /etc/X11/xorg.conf from here somehow??

---

### Post by fakie_flip on 2007-03-26
yes, you can edit your /etc/X11/xorg.conf in text mode. there are a few command line text editors and the easiest for you to use is nano. a more advanced one is vim, but it takes time and practice to learn it.

sudo nano /etc/X11/xorg.conf

use control w to save and control x to exit.

---

### Post by fakie_flip on 2007-03-26
before making any changes to your xorg.conf, i recommend that you make a backup copy to be safe. use this command.

sudo cp -v /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

---

### Post by annda on 2007-03-26
you can do it from live cd but that is a bit more difficult (you have to mount your filesystem first), and it will probably take more time for you.

---

