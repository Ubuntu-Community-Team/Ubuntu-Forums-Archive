---
title: "Where are Session Preferences (9.04)?"
date: 2009-05-14
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-14
In my System>Preferences menu there is no submenu for Sessions. I'm reading the Ubuntu Pocket Guide and would like to change some settings but I can't find the Sessions prefs. Did they move it, and if so, where is it now?

PPC G4 Sawtooth, Ubuntu 9.04

---

### Post by netJackDaw on 2009-05-15
It is in the same menu but renamed to "Startup Applications", which i think is more appropriate. Still I had the same problem as you finding it first. Names you are used to stick even if they are bad choices...

---

### Post by Benboom on 2009-05-15
Thanks! I had searched the forum but couldn't find that info anywhere, althuogh I suspect everything is there if you can only use the right search terms.

---

### Post by stream303 on 2009-05-15
Be careful in there.  Be sure to research what you are planning to disable.

Since I don't use Evolution, I always uncheck the Evolution Alarm notifier..

---

### Post by Benboom on 2009-05-15
All I took out was the Evolution monitor, Bluetooth, and the Gnome login sound and splash screen. It seems to be working fine so far. I just wanted to get anything I didn't actually use out of the system but there really isn't that much in the Startup Items list. I'm sure there's more somewhere but at this point I'm not going to go poking around under the hood too much. :D If it ain't broke, don't fix it.

---

### Post by pawnrocket on 2009-06-02
If those are the Start Programs how do you adjust the priority of said start up programs.

I want <program1> to start before <program2>

any ideas?

---

### Post by pawnrocket on 2009-06-03
bump

I want to adjust the priority of startup processes

---

### Post by pawnrocket on 2009-06-03
Nevermind

I wrote a scripted and included

```
sleep 10
```

Then created gnome-sessions called <program1 and program2>

program1 executes on login
program2 is the script and is forced to sleep insuring that it is loaded after program1

I think we should be able to set priority in gnome-sessions and not have to work around. 

Thanks,

r3L1c

---

### Post by cyberdork33 on 2009-06-04
[https://bugs.edge.launchpad.net/gnome-session/+bug/32194](https://bugs.edge.launchpad.net/gnome-session/+bug/32194)

---

