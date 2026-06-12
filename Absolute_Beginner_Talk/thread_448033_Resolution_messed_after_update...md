---
title: "Resolution messed after update.."
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by TehSnarf on 2007-05-18
So I did some sort of update.. I believe Beryl was involved. I rebooted the computer because it seemed like the hip thing to do, and now my resolution is stuck at 800x600, with the only other option at 640x480. I checked my /etc/X11/ directory for backups to the xorg.config file, and there's one named xorg.conf.backup.beryl-script... so I copied xorg.conf to xorg.conf.orig, copied the .backup.beryl-script to xorg.conf, restarted GDM via /etc/init.d/gdm restart, but no dice. Not quite sure what to do at this point, but previous to all this updating shinanigans I could choose from a whole slew of resolutions. Any idea what I may be overlooking?

---

### Post by TehSnarf on 2007-05-18
After doing some investigating, seems that for some reason my xorg.conf file lost my monitor refresh information. Did some searching on the internets, found the information, and put it in. Seems to work like a champ now!

---

