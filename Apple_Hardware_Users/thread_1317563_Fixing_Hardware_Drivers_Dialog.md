---
title: "Fixing Hardware Drivers Dialog"
date: 2009-11-06
forum: Apple Hardware Users
---

### Post by Cerin on 2009-11-06
After following some guides in this forum, my "Hardware Drivers" dialog is now completely unusable. Trying to activate or deactivate any drivers results in the "SystemError: installArchives() failed". Googling this text only shows open bug reports, so it looks like no one has ever publically succeeded in fixing this error.

Other than non-working wireless, everything else on my system is actually working perfectly, so I'd like to avoid having to blow everything away and do a fresh install. Is there anyway I can fix this error, so I can continue to debug my wireless problem?

---

### Post by pastalavista on 2009-11-06
Try this in terminal ```
sudo aptitude reinstall jockey-common jockey-gtk
```

What kind of wireless card do you have?

---

### Post by Cerin on 2009-11-06
I fixed the problem by doing:

modprobe -r wl

to remove the proprietary wireless driver. I also removed it from /etc/modules. Not sure why that would have blocked the dialog, but it works perfectly again.

---

### Post by Cerin on 2009-11-06
@pastalavista

I have whatever comes with the MacbookPro5.5.

---

