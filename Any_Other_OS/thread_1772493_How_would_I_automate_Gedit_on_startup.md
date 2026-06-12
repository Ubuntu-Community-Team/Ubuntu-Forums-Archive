---
title: "How would I automate Gedit on startup?"
date: 2011-05-31
forum: Any Other OS
---

### Post by Rytron on 2011-05-31
Hello.

I'd like automatically Gedit to open on startup and load my saved gedit session. Would autokey or some other program do this?

I ask as Linux Mint 11 wont save open applications when I shut down.

Thanks.

---

### Post by Rytron on 2011-06-12
I noticed this when playing around with gedit commands in the terminal.
What would I put instead of '**FILE**' in this? Would that load my last session? If so I could add that command to 'Startup Applications'.

```
gedit --sm-client-state-file=FILE
```

---

### Post by pqwoerituytrueiwoq on 2011-06-12
gedit has a restore session addon
edit->preferences->addons->session saver
you may need the [FONT=Courier New]gedit-plugins[/FONT] package

---

### Post by Perfect Storm on 2011-06-13
Moved to Other OS/Distro Talk.

---

### Post by Rytron on 2011-06-13
> **pqwoerituytrueiwoq said:**
> gedit has a restore session addon
edit->preferences->addons->session saver
you may need the [FONT=Courier New]gedit-plugins[/FONT] package

Hi. Yes, I always use Gedit session saver. In Ubuntu 11.04 based distros such as LM 11, open applications cannot be saved. I want to add a line to '**Startup Applications**' with something like ```
gedit --sm-client-state-file=**FILE**
```
The name of my saved session is **[COLOR="Indigo"]01[/COLOR]**. I don't understand how to complete the above code and would like to know what goes in place of **FILE**?

---

### Post by Rytron on 2012-05-03
This is what I refer to. I'd like a command that would automatically do this on login. To load the saved last session, in this case it is titled '1'.

---

