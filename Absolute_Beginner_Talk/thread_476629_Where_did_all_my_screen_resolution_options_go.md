---
title: "Where did all my screen resolution options go?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-17
i was viewing my xorg.conf file and typed  the following command:

```

 sudo dpkg-reconfigure -phigh xserver-xorg

```

I tried to escape from this area because it looked like a bad place for  a noob like me to be but there was no "exit without saving" button to push.  anyways after i rebooted I only had 3 screen resolution options.

My efforts to get Beryl running and dealing with this expensive ATIx1900xtx video card keep getting me deeper into a graphics hole that I cant get out of.  If I cant get my resolution choices back, what can I do to restore Ubuntu initial video settings?

Thx,

VC

---

### Post by w4ett on 2007-06-17
> **videocheez said:**
> i was viewing my xorg.conf file and typed  the following command:



I tried to escape from this area because it looked like a bad place for  a noob like me to be but there was no "exit without saving" button to push.  anyways after i rebooted I only had 3 screen resolution options.

My efforts to get Beryl running and dealing with this expensive ATIx1900xtx video card keep getting me deeper into a graphics hole that I cant get out of.  If I cant get my resolution choices back, what can I do to restore Ubuntu initial video settings?

Thx,

VC

WELL, what you need to do is to go back into the terminal and type: 

 sudo dpkg-reconfigure -phigh xserver-xorg  

and complete the configuration.

Select the original driver and also the resolution/refresh rates that you desire  (up and down arrow keys move cursor, spacebar selects options, enter confirms selections)...unless you backed up your original xorg.conf file before attempting any changes.  If you backed up....restore the backup file.

---

### Post by videocheez on 2007-06-17
> **w4ett said:**
>  If you backed up....restore the backup file.

Awesome.  I knew somebody would help me.  I didn't realize that the space bar needed to be hit. :D

Also for future reference.  How do I restore the original file?

---

### Post by w4ett on 2007-06-17
the command is:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

### Post by videocheez on 2007-06-17
Thanks man.

---

### Post by w4ett on 2007-06-17
No Problem...we're here to help.

---

