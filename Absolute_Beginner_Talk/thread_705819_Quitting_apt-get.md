---
title: "Quitting apt-get??"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by hungryhamster on 2008-02-23
Im trying to install a printer, and I downloaded hplip to help that process. however, in the auto-setup after running "sh hplip-2.8.2.run", after downloading the file, it tells me that a package manager apt-get is running and I should quit it. im pretty sure that this is prohibiting me from progressing.... however I was under the impression that apt-get only ran when I said so in terminal? confused!! I cant open synaptic either cause it gives me sort of the same message... 

> "Unable to get exclusive lock

This usually means that anotyher package management feature (like apt-get or aptitude) is already running. Please close that application first."

terribly confused! I would appreciate any and all help.

---

### Post by jpeddicord on 2008-02-23
You may want to try simply restarting and then running the setup script again. That should free up the lock.

---

### Post by JoshuaRL on 2008-02-23
Do you have Add/Remove open, or are you installing updates?  If you have it set to install and/or download security updates automatically then that might be the issue.

If not, try to restart the machine and see if that helps.

---

### Post by Dr Small on 2008-02-23
Try restarting to get rid of the lock.

---

### Post by hungryhamster on 2008-02-23
thanks all for your help! it worked... I should have thought of that myself, being a windows user :P

---

