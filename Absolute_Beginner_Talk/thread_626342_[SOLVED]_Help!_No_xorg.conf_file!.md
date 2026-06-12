---
title: "[SOLVED] Help! No xorg.conf file!"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Canew on 2007-11-29
Ok, my xorg.conf file appears to be missing. Yes, I deleted it while installing Gutsy off the standard Live CD in order to get a GUI for the install. I assumed the CD would replace/create a proper xorg.conf file. Apparently this didn't happen. How can I make one, and why am I able to start X without one? 

Doing sudo locate xorg.conf generates this:

```
/usr/share/xresprobe/xorg.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablenvidialogo
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablectrlaltbackspacegnome
/usr/share/displayconfig-gtk/xorg.conf.fallback
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster

```

Please help!

---

### Post by vikramsharma on 2007-11-29
When you boot into Ubuntu recovery mode, type "sudo dpkg-reconfigure xserver-xorg" in the terminal without the quotes (you would have to be logged in as root, sudo would be good enough too).  You could boot with the live Ubuntu cd and copy the xorg.conf from the cd to hard drive (/etc/X11).

---

### Post by Canew on 2007-11-29
Fixed, but only after a small adventure...

First, I had done "sudo dpkg-reconfigure xserver-xorg" after using Envy to install the driver. That, and other similar reconfiguration tools/commands was what led me to discover the lack of the xorg.conf file. As I said, I had deleted it while booting from the LiveCD, as that was the only way to use the original LiveCD to do a GUI-based install. Doing it with the xorg.conf file in place gave me the "black screen of death."

After trying a few times to reconfigure x, I ended up doing a reboot, and lo and behold, I got the black screen again! Ctrl+Alt+F1 and a quick search later, and bingo! xorg.conf was back! Not sure how it happened, but it did! So to get back to X and the GUI, I copied it, deleted the original (again), restarted X as root (GUI popped back up again), then went into the terminal, and restored my xorg.conf file from the copy I'd made. Finally, went and tried all the reconfig tricks I was trying to do in the first place, and they all worked!

Long story short: My drivers are now fully updated, not even a hiccup. Now, BZFlag works, albeit without sound (but that's another thread), and I got at least one game (DoW: Winter Assault, if anyone cares) working through Wine flawlessly! WAY kewl! Gutsy works better on my computer than Edgy did by far! :)

---

