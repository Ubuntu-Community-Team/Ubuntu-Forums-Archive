---
title: "Another networkintg problem"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-08
yesterday i got  my net right after switching off IPv6.but now each time i start ubuntu i need to reboot it again so that FF shows something....

---

### Post by pardesi on 2007-06-09
someone please:(

---

### Post by p_quarles on 2007-06-09
I'm not 100% sure what you mean. Are you saying that Firefox needs to start, close, and then start again before it connects to anything? Are you restarting your desktop GUI? Or are you rebooting the entire system?

---

### Post by pardesi on 2007-06-09
i am rebooting the entire system

---

### Post by p_quarles on 2007-06-09
That's kinda strange. Let me see if I've got it right:

--You start up the system
--You open Firefox, and it won't connect to the internet
--You restart the system
--Firefox connects to the internet

Sounds like this problem is way beyond my understanding. Just for kicks, though, have you tried rebooting the GUI (ctrl-alt-backspace or "Log Out")? If not, try that and see if has the same effect.

---

### Post by pardesi on 2007-06-09
yes that's very strange:(

---

### Post by p_quarles on 2007-06-09
Did you try reloading Gnome/KDE? Please do, because even if it doesn't solve the problem, it would help diagnose it.

---

### Post by pardesi on 2007-06-09
isn't there a method to update the file which i changed.so that each time i do not have to save it and reboot....

---

### Post by pardesi on 2007-06-09
someone....

---

### Post by zvacet on 2007-06-09
Wich file you changed and want to update?Does you connection worked properly before changes?

---

### Post by pardesi on 2007-06-09
i changed the 
```
\etc\modprobe.d
``` to switch off my IPv6
i need to restart my computer each time after starting to get the FF working ....
the net was working fine some two days back then it the FF won't load any pages though the connection would be there.so needed to fix it so i switched off the IPv6  so i think though i saved the change it's the updating of root file that's creating this problem.hope so...

---

### Post by Atomic Dog on 2007-06-09
Did you try turning off ipV6 in FireFox?  Type about:config in the address bar and try turning it off there too.

---

### Post by pardesi on 2007-06-09
yes i did that too and yet i have to res:(tart...

---

### Post by pardesi on 2007-06-09
someone please it's really getting fussy:(:(

---

### Post by zvacet on 2007-06-10
Did you remember what is etc/modprobe.d look before you changed it?If you do try to put it back and after that we will see where problem is.

---

### Post by pardesi on 2007-06-10
it was empty ....and when it was wmpty i was unable to connect ....

---

