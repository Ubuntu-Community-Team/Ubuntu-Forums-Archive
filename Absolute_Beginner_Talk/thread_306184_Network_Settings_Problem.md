---
title: "Network Settings Problem"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Padraig Notlad on 2006-11-24
I'm new to Ubuntu, and have just wanted to rename my computer.  I did, and now my DNS settings won't save.  This is driving me crazy.  Does anyone know why DNS doesn't save after reboot?

---

### Post by punx45 on 2006-11-24
if you renamed it the wrong way, the settings dont stick.   how did you rename it?

---

### Post by Padraig Notlad on 2006-11-24
Well, the first time I renamed it, I only changed the /etc/hostname file.  Then I couldn't do anything, and realized I also needed to rename the /etc/hosts file.  Then everything seem alright, except that DNS settings don't stay if I reboot.  So then I decided to rename the computer again using  System -> Administration -> Networking -> General -> Hostname, then rebooted again, and still DNS don't stay.  Is there somewhere else?

---

### Post by punx45 on 2006-11-25
no i think using the administration menu is the correct way. im pretty sure that is how I did it.

---

### Post by Padraig Notlad on 2006-11-25
O.K. problem fixed.  I figured it out.  I had created a location in network settings, and that must have been associated with the old computer name when I did it wrong.  I deleted that location, and am now able to retain network settings.

---

