---
title: "Gnucash anyone..."
date: 2005-01-31
forum: Apple PPC Users
---

### Post by ram on 2005-01-31
Hi, 
   Has anyone been successful in running gnucash on warty ppc. 
My installation went through fine (apt-get install gnucash installed about 47 packages) but it crashed as soon as I tried opening the Preferences menu. It crashed in /bin/guile. The currencies are do not show up on screen (it is shown as <.> instead of the usual dollar). Am I missing something here. Has anyone similar problems. Please let me know if someone knows a workaround.

-cheers-
Ram

---

### Post by Viro on 2005-01-31
It works fine on my machine. What kind of .currency are you using? Mine is set to the Great British Pound £.

---

### Post by ram on 2005-02-01
OK. This issue is solved now. Guile seems to crash for some reason if the locale is set to en_IN (for India). I reset the locale to en_US and gnucash stopped crashing.

---

