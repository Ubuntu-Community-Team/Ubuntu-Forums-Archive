---
title: "Automatic Update Notifier not working"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Baasha on 2006-08-15
When I initially installed Dapper from the iso cd one of the first things it did after starting up was to turn on the little icon in the top panel and told me there was an upgrade ready to be d/l.

Since then I have never had that happen again, even though there have been several upgrades.  I always have to do a manual check and then d/l the latest upgrades.

Does anyone have any ideas what might be wrong?

---

### Post by avtolle on 2006-08-15
Check under Sytem->Preferences->Sessions, Startup Programs Tab to see if update-notifier is listed;if not, add it.

---

### Post by Baasha on 2006-08-15
update-notifier is listed in the startup programs tab.  In my Home folder there is a hidden directory .update-notifier but it is completely empty.  Should there be some files in there?

---

### Post by confused57 on 2006-08-15
You could check System---Administration---Software Properties
and see if your system is set up for automatic updates.
I'm not on Ubuntu right now, but I think that's right.

---

### Post by ComplexNumber on 2006-08-15
> **Baasha said:**
> When I initially installed Dapper from the iso cd one of the first things it did after starting up was to turn on the little icon in the top panel and told me there was an upgrade ready to be d/l.

Since then I have never had that happen again, even though there have been several upgrades.  I always have to do a manual check and then d/l the latest upgrades.

Does anyone have any ideas what might be wrong?
right click on the panel, select Add to Panel. then scroll down to the Notification Area and add it to the panel.

---

### Post by bhoughton on 2006-08-15
I too have this problem.  Notification area is there, check daily in "software properties" is checked and update is a startup program in sessions.

Any further suggestions appreciated.

Regards...

---

### Post by confused57 on 2006-08-16
> **bhoughton said:**
> I too have this problem.  Notification area is there, check daily in "software properties" is checked and update is a startup program in sessions.

Any further suggestions appreciated.

Regards...

Looks like you have everything set up correctly for automatic update notification...do you have the universe & multiverse repositories enabled?
You'll probably have more updates with the extra repositories enabled.
  Occasionally, I'll open Synaptic Package Manager, and click on "Reload", then "Mark All Upgrades",(then "Apply", if there any upgrades) for what that's worth.

---

### Post by Jaybird on 2006-08-25
I believe that you must ensure you have a notification area on your panel as mentioned above and likewise system-administration-software properties-internet update is checked, but also that adept is installed.  Go to Synaptic and search on adept.  You may have to re-install it by removing it and then install.

---

