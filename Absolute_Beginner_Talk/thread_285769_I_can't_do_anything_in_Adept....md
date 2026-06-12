---
title: "I can't do anything in Adept..."
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Contrast on 2006-10-27
Whenever I log into Adept Package Manager, I get this message in a dialog window labeled "Read Only mode: Database Locked - Adept Manager":
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

I've tried restarting my computer multiple times and have checked the task manager for programs that might be using the database with no success. Could someone please help me out with this? (Keep in mind that I have very little experience with the command line, so if your suggestion includes use of it, please tell me exactly what to type for each command. Thanks.)]

---

### Post by Rackerz on 2006-10-27
What programs do you have running when you start up? Maybe the update manager is running?

---

### Post by megadyptes on 2006-10-27
Had a similar problem, the discussion in [http://ubuntuforums.org/showthread.php?t=206634](http://ubuntuforums.org/showthread.php?t=206634) seemd to cover it, and helped sort the issue.

---

### Post by Contrast on 2006-10-27
> **megadyptes said:**
> Had a similar problem, the discussion in [http://ubuntuforums.org/showthread.php?t=206634](http://ubuntuforums.org/showthread.php?t=206634) seemd to cover it, and helped sort the issue.
Beautiful. "sudo dpkg --configure -a" got it. Much appreciated.

---

