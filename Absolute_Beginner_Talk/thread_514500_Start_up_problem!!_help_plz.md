---
title: "Start up problem!! help plz"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by smalss on 2007-07-31
When i try to start up Ubuntu i get this error:

Failed to start the X server

Then it just goes to the terminal. How can i fix that?? Something to do with the graphics card?

---

### Post by yorkie on 2007-07-31
open terminal tthen type

  sudo  dpkg-reconfigure xserver-xorg 
then reboot

---

### Post by Rocket2DMn on 2007-07-31
> **yorkie said:**
> open terminal tthen type

  sudo  dpkg-reconfigure xserver-xorg 
then reboot

Indeed, it is probably a driver problem, so reconfiguring the Xserver will give you the option to select the correct video driver and screen resolution options.  You don't actually need to reboot.  If the Xserver was running you would do CTRL+ALT+BACKSPACE, but since it's not, you just run one of these commands when the reconfiguration is complete
```
/etc/init.d/gdm start
   or
startx
```

---

### Post by pollywog on 2007-07-31
It sounds like your file /etc/X11/xorg.config got messed up. That kills X(the foundation of your GUI). When you find yourself at the command line try editing this by running
```
dpkg-reconfigure xserver-org
```

you may have to add "sudo" in front of this command- I can't remember.  If you go thru this procedure a couple of times without fixing the problem you may be able to rescue the system from outside using your fiesty disk.

---

### Post by smalss on 2007-07-31
thnx guys.. i'll try all that stuff tonite!

---

