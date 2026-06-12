---
title: "Problems removing autostart"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by mikkelrev on 2007-08-11
Hey, 

I have a problem. Whenever I log onto Ubuntu, the File Browser and Skype opens, but I don't want them to. I've checked through Sessions, and they are not listed as autostart, and I've also checked through both File Browser and Skype's settings, looking for something similar to "Run on startup", but I haven't found anything. 

So, how do I remove these two from starting up when I log in? It's a bit annoying. :-|

---

### Post by schorsch on 2007-08-11
System -> Preferences -> Sessions -> Session Options --> Automatically save changes to session

If this is checked, the current state is saved when the OS is shutdown. So any running Firefox, Skype or whatever will be reloaded at next startup. 

So you should uncheck this button and to be on the safe side: There is a button entitled "Save the current session". Do this when nothing is running and this clean session will be started on every startup.

---

### Post by mikkelrev on 2007-08-11
Thanks alot, worked like a charm. :)

---

### Post by schorsch on 2007-08-11
Glad to hear that. You're welcome ....:)

Ah, and please mark this thread as solved .....

---

