---
title: "Ghost box thing...HELP!!!"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Phiber_tek on 2007-12-06
So whenever I use the package installer thing, just when I click it under system>preferences, right away this box comes up in the middle of the screen, theres nothing its just a transparent box, the only way I notice is because my theme casts a blue back light, so I see this blue backlight all the time after I use the installer software, even when I open new windows and like firefox, anything it never goes away...so I'm getting annoyed at it, anyone ever heard of this?

---

### Post by Slim Backwater on 2007-12-06
That's probably gksu or gksudo prompting you for your password to do administrative tasks.  I had the same problem with an old laptop but never found a solution for it.

This might help:
[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/91151](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/91151)

Try updating from the terminal (accessories -> terminal) "sudo apt-get update" "sudo apt-get upgrade".


HTH

._.

---

### Post by kiwirobin on 2008-03-07
Played around with compiz settings and turning off negative under Accessibility got rid of it for me.
:)

---

