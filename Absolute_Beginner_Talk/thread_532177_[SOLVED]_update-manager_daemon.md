---
title: "[SOLVED] update-manager daemon?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by forger on 2007-08-22
what's the process name of the update-manager daemon? I mean The one in the notification area that notifies you that you have updates waiting?

Because it never notifies me of anything, I have to sudo apt-get update and then upgrade to check and/or do updates

edit: ok found it, it's update-notifier, but should I add it in gnome sessions?

---

### Post by scrooge_74 on 2007-08-22
you can configure it to behive the way you want: when to look for upgrades, how to install them etc

---

### Post by forger on 2007-08-22
and.. how do i do that? :) can i set to every 12 hours?

---

### Post by scrooge_74 on 2007-08-22
go to System >Admin >Software origins > Updates 

check for updates to be daily and you can set if you want it to download and install them or just notify you.

The other way is to make a CRON job by yourself (but this is what the above actions do anyway)

Any doubt let me know

---

### Post by bapoumba on 2007-08-22
You also have to add a "system tray" (not sure how it's called in GNOME) to the panel. Right clic on the panel, and add the systray.

---

