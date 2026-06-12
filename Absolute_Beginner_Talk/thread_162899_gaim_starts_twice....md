---
title: "gaim starts twice...?"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-19
whenever i restart or boot up, gaim has two icon in the sys tray, one logs me on automatically, (which I want) and another just doesnt log on, im guessing because one is on already, how do I make only one come up?

---

### Post by 5-HT on 2006-04-19
Did you accidentally add it to the startup programs list twice?
If so, just removing one occurance of it there should do the trick.

---

### Post by x5452 on 2006-04-19
no, it is only listed once in sessions>starup

---

### Post by 5-HT on 2006-04-19
Here's a shot at the dark...but what about closing all instances of GAIM, saving your session, and logging back in?

---

### Post by Mustard on 2006-04-19
[QUOTE=5-HT]Here's a shot at the dark...but what about closing all instances of GAIM, saving your session, and logging back in?[/QUOTE]

Ah good thinking. :)  I reckon you have worked that one out. :)

---

### Post by richardward101 on 2006-04-19
I think I may know whats happening here as it happened to me. When you log out there is an option to select that says "save session." this saves all running programs and relaunches them at startup. If you select this at log out and also have it as a startup program then Gnome will log you in, restore Gaim from your saved session and then run it again as a startup program. To fix it run system->preferences->sessions, and delete the "Default" session, then use ctrl+alt+backspace to restart Gnome, and it should be fixed, If this isn't it then i'm afraid i don't know :???:

---

### Post by 5-HT on 2006-04-19
[quote=Mustard]Ah good thinking. :)  I reckon you have worked that one out. :)[/quote]

Let's hope so. :D
From richardward101's post, looks like that did it for him.

---

### Post by x5452 on 2006-04-19
wow lots of advice while i was gone reading and confusing myseld with grub splash screens, lol.  
as far as sessions go, when i first got ubuntu set up i went into sessions tab ans told it to always save settings as I leave, and also i have gaim in startup, but usually when i log out i have gaim running and it just gets closed as i log out. do youthink that is why it comes on twice? becuase i have it on 'always save settings' so it turns it back on when i reboot?

---

### Post by 5-HT on 2006-04-19
[quote=x5452]wow lots of advice while i was gone reading and confusing myseld with grub splash screens, lol.  
as far as sessions go, when i first got ubuntu set up i went into sessions tab ans told it to always save settings as I leave, and also i have gaim in startup, but usually when i log out i have gaim running and it just gets closed as i log out. do youthink that is why it comes on twice? becuase i have it on 'always save settings' so it turns it back on when i reboot?[/quote] 
If you save your sessions with it running and also have it set up to start automatically, that definitely could be a possibility.

If you always save your sessions, best thing to do would be to remove GAIM from the startup services.

---

### Post by x5452 on 2006-04-19
excellent, thanks a bunch everyone, thats double thing was getting waaayy annoying :mrgreen:

---

