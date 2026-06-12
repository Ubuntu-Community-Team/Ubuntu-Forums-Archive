---
title: "Help with Graphics Drivers"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-02-08
Okay, I am going to take the plunge and attempt to upgrade my graphics drivers to the ATI ones.    First off, let me say that I have an ATI Radeon Express 200 card (it is a recent integrated graphics card).  It is my understanding that I can get the driver from the repositories (my card isn't too new, is it)?  After that, one needs to reconfigure the X Window Server to use those graphics drivers.   So, my plan of action seems to be:

1. Make a copy of the configuration file (whatever it is called and wherever it is stored).
2.  sudo aptitude install [driver name here]
3. Edit the X configuration file to use the new driver.
4. Reboot.
5. If the system fails to boot properly, [do something here to revert to the copy of the config file]
6. Play Tuxkart.

Is this a sound plan?  Would anyone be so kind as to help me flesh out the details?  I know there is a command for reconfigure X, but I'd rather not do that because it has detected everything properly so far and I don't know the answer to some of its questions like Sync rate, so just using what it has now minus the driver would be ideal.  :popcorn:

---

### Post by Sqwishy on 2007-02-08
the file you wana edit is located in /etc/X11/xorg.conf :] hope it works

---

### Post by Darklighter137 on 2007-02-08
Thank you very much!  I would be happy if anyone had any further suggestions about my plan.

---

### Post by Maestro23 on 2007-02-08
> **Darklighter137 said:**
> Thank you very much!  I would be happy if anyone had any further suggestions about my plan.

This is the guide I used for my ATI card.  Worked like a charm.

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by Darklighter137 on 2007-02-08
Thank you!

---

