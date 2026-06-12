---
title: "Is there a &quot;startup applications&quot; equivalent for OSX? Need to run command at login..."
date: 2012-03-21
forum: Any Other OS
---

### Post by Roasted on 2012-03-21
In Ubuntu, I have an rsync command tagged in Startup Applications. When I log in, it runs, and my data gets synced to my file server. Beautiful!

I'm trying to figure out how I can do the same thing on my Macbook Pro. I found a way that sort of works, by writing a #!/bin/bash script, chmod +x it, set it to launch with terminal, and then going system preferences - accounts - my user - login items - and adding it to the login item list. 

I can't help but to think there's an easier way that I'm not thinking of. Any ideas?

---

### Post by papibe on 2012-03-21
Hi Roasted.

I'm almost sure they have 'cron'. You can 'crontab -e' to create one. Then, if they have similar keywords, you would be able to create a rule using '@reboot' that means 'run once at startup'

Just and idea.
Regards.

---

### Post by Roasted on 2012-03-21
> **papibe said:**
> Hi Roasted.

I'm almost sure they have 'cron'. You can 'crontab -e' to create one. Then, if they have similar keywords, you would be able to create a rule using '@reboot' that means 'run once at startup'

Just and idea.
Regards.

Wait... is that to say that you can use @reboot and whatnot in the Linux cron??

I do believe OSX has cron, but I never knew you could do anything with cron other than schedule a specific time. Since I'm not turning my computer on at the SAME time every day this was a concern of mine. But if I can rig up cron to do run at a more dynamic time (login, startup, etc) this may work...

---

