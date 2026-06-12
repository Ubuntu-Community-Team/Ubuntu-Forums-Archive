---
title: "firefox update problem"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-11
in the "help" colum the "check for updates" is greyed and I cannot click on it.
how to update firefox ???

---

### Post by avtolle on 2006-07-11
AFAIK, the version of Firefox after the last update (2 weeks? 1 month?) ago is the latest version in Dapper. To answer the question I suspect you are really asking, it is my understanding that the version of Firefox supplied through the repos has been patched by the Ubuntu devs to run better w/the system. I recall the rush to update to 1.5.03 before Dapper was released, and there were serveral "How-Tos" floating around at that time. So, I guess you should be on the lookout for new Firefox versions, and posts to the Forum.:)

---

### Post by chickengirl on 2006-07-11
I suspect it's because you don't have write permissions for the Firefox directory (because you're running as a regular user and Firefox isn't installed in your /home).

But don't worry about it, because checking for updates is Update Manager's responsibility, not yours. When you have updates available you'll see an icon in the notification area ("system tray" in Windows-speak). Click on it and you'll take care of updates from there.

---

### Post by Anduu on 2006-07-11
Update for Firefox is disabled by default.

You can cheat and get updates for Firefox by entering sudo firefox in a terminal window.Once updated close Firefox and run as you normally would(ie from the menu...)Do not run firefox with sudo for everyday use.

Be warned however updating this way will lose all your bookmarks and settings....be sure to back them up!

---

### Post by ShirishAg75 on 2006-07-11
There's supposed to be a 1.5.0.5 in the offing somewhere. It would be nice to update to that.

---

### Post by MaximB on 2006-07-12
> **Anduu said:**
> Update for Firefox is disabled by default.

You can cheat and get updates for Firefox by entering sudo firefox in a terminal window.Once updated close Firefox and run as you normally would(ie from the menu...)Do not run firefox with sudo for everyday use.

Be warned however updating this way will lose all your bookmarks and settings....be sure to back them up!

if it's disabled - will the update manager find firefox updates for me ?

---

### Post by chickengirl on 2006-07-12
> **MAXDDARK said:**
> if it's disabled - will the update manager find firefox updates for me ?

Yes. Like I said, in Ubuntu checking for Firefox updates is not your job, it's Update Manager's.

---

