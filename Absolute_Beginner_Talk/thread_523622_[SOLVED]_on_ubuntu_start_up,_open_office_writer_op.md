---
title: "[SOLVED] on ubuntu start up, open office writer opens...why?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by snuffy on 2007-08-12
When i start up ubuntu and log in, open office automatically starts a writer page.  i have looked in system > preferences > sessions, and with open office closed, clicked 'save current session' but this doesn't stop it starting when i log in.

i don't really know what to search for, in order to prevent this, so am a bit stuck.

please help.

---

### Post by arijarot on 2007-08-12
The only think that I can think of is that under system>preferences>sessions, on the "startup program" page tab, you should (by my logic) have a command enabled under the additional startup programs to open office at the startup. you would either need to disable it (un-tick it) or delete it to prevent office from opening.

---

### Post by snuffy on 2007-08-12
> **arijarot said:**
> The only think that I can think of is that under system>preferences>sessions, on the "startup program" page tab, you should (by my logic) have a command enabled under the additional startup programs to open office at the startup. you would either need to disable it (un-tick it) or delete it to prevent office from opening.


i have tried to remove the following line from sessions > current session:

ooffice -quickstart -nologo -nodefault

but when i log off and back in again, this line reappears in the current session box, and writer starts again.

---

### Post by arijarot on 2007-08-12
IMO, I don't think that line has anything to do with opening open office at startup. Is there no entry enabled under sessions>startup programs>additional startup programs to open open office?

---

### Post by snuffy on 2007-08-13
> **arijarot said:**
> IMO, I don't think that line has anything to do with opening open office at startup. Is there no entry enabled under sessions>startup programs>additional startup programs to open open office?

ahh, yes, sorry, misread your last post. 

i had the openoffice quickstarter app in there. i removed it and now the problem is fixed. its weird that i have had the quickstarter installed for some time now and it's been fine until recently when it seems to have begun to open a blank writer doc every time i log in.  

oh well, i can live without the quickstarter. 

thanks for your help arijarot.

snuffy.

---

