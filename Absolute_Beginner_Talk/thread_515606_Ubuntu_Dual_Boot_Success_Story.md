---
title: "Ubuntu Dual Boot Success Story"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by flamingsole on 2007-08-02
Hello,

So, for the past week or so, I have endured various trials in attempting to dual boot XP and Ubuntu. The other night, I finally succeeded in getting it working, and thought I would share my story.

I've posted on here several times concerning the issues I was having, as XP refused to boot, or Ubuntu refused to boot, or both of them refused to boot. My successful attempt went as follows:

[LIST=1]
[*]Re-Download Ubuntu Desktop Installer, try again with new CD.
[*]No luck.
[*]Download Ubuntu Server Installer, check CD for errors, continue.
[*]Follow installation instructions, giving the slave drive to Ubuntu, while the master drive ran XP.
[*]Allow Ubuntu to install GRUB on the master drive.
[*]Follow the rest of the instructions, reboot system.
[*]Ensure that Windows still worked, reboot again.
[*]Log in to Ubuntu, watch things happening on the black screen.
[*]Enter sudo apt-get install ubuntu-desktop to install GNOME gui.
[*]Watch more installation, reboot again.
[*]Feel good about myself.
[/LIST]

Thanks for all the help in these endeavors!
Jonathan

---

### Post by LaRoza on 2007-08-02
Glad you got it working, but it shouldn't have been so difficult.

---

### Post by az on 2007-08-02
Don't forget to install the desktop kernel, too.  The server kernel does not work with a lot of desktop hardware

sudo apt-get install linux-generic

How much ram do you have?  The live cd installer needs at least 256 megs.

---

### Post by flamingsole on 2007-08-02
I have a gig of ram.

---

