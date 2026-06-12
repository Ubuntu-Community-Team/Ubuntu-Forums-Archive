---
title: "Help I deleted a panel and can't get it back ! :s"
date: 2009-03-25
forum: Art &amp; Design
---

### Post by Ben Crisford on 2009-03-25
Stupidly just now, I was playing about with my appearance and I deleted the bottom panel, which means whenever I minimise anything i cant get it back, even after half an hour and several cups of coffee.

Here is my desktop now:

---

### Post by s.fox on 2009-03-25
Right click on the top panel. I think there is an option called 'Add New Panel' -> 'External Taskbar' or something like that. 
 
Or just select 'Add New Panel' then on that new panel right click and select 'Add Applet to Panel' and then select which ever you want like tasklist/windows list, desktop icon, trash icon etc...

I would check myself but I am using OSX at the moment .

---

### Post by UbuntuNerd on 2009-03-25
use this command in a terminal to restore your panels to default:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by Ben Crisford on 2009-03-25
It worked, but it deleted all my shortcuts :(.

Nevermind though, because I can put them back in seconds, so cheers loads ubuntunerd :D:D:D.

@Ash R, there is no add new panel that I could see, but there was an add to toolbar button which was as good as, so if I found no solution I could have put my window navigation on the top toolbar so thanks :D.

---

### Post by s.fox on 2009-03-25
Glad you got it sorted.  Remembering stuff like that is hard :lolflag:

---

### Post by Chemical Imbalance on 2009-03-25
> **Ben Crisford said:**
> It worked, but it deleted all my shortcuts :(.

Nevermind though, because I can put them back in seconds, so cheers loads ubuntunerd :D:D:D.

@Ash R, there is no add new panel that I could see, but there was an add to toolbar button which was as good as, so if I found no solution I could have put my window navigation on the top toolbar so thanks :D.

Its called "New Panel"

---

### Post by UbuntuNerd on 2009-03-25
> **Ben Crisford said:**
> It worked, but it deleted all my shortcuts :(.

Nevermind though, because I can put them back in seconds, so cheers loads ubuntunerd :D:D:D.

@Ash R, there is no add new panel that I could see, but there was an add to toolbar button which was as good as, so if I found no solution I could have put my window navigation on the top toolbar so thanks :D.

I should have told you that you would have to add all your shortcuts back, but like you said you can add them back in a second.

---

### Post by badmedic on 2009-03-25
You could also just add "Window List" and whatever other gnome applets you want to the top panel and live without a bottom panel... It frees up a little more desktop real-estate. :)

---

### Post by smartboyathome on 2009-03-26
Another tip, use Alt+Tab, it switches between windows. :)

---

