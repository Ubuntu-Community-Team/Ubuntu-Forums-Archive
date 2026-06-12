---
title: "gkrellm configuration?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-18
I just installed gkrellm through synaptic, when i started it, (through the menu) it said I could read the config file for help on configuring.  where is the file?  I cant find where gkrellm was installed to... 
Im hoping, does anyone know, is there a way to NOT have gkrellm appear in the windows open selector list..just to have it come on with boot, and run, without having a tab for it?
also if anyone knows where an active link is to the invisible theme, I would be grateful.  IM assuming the config, (if i find it) tells how to install new themes....? THanks for your time!

---

### Post by trent dillman on 2006-04-18
The config should be in /etc somewhere (like /etc/gkrellm) or in /usr.

This will help you find it:
```
sudo updatedb
locate gkrellm
```

Also, for pinning and making your window list ignore gkrellm, install devilspie and configure it for gkrellm.

---

### Post by taurus on 2006-04-18
Themes are here, [http://www.muhri.net/gkrellm/](http://www.muhri.net/gkrellm/)...

---

### Post by x5452 on 2006-04-18
sweet just got it going, ( i was sending the tar to gkrellm not gkrellm2) so it wasnt working, oops. ](*,)  does anyone know though about getting rid of the gkrellm in the "window list" area?  seems there should be a way for it to just 'run in the background' all the time, and not be in the window list...follow me? :confused:

---

### Post by trent dillman on 2006-04-18
Sure...

Install devilspie, then make a folder in your home directory named .devilspie.
Then, make a file inside called 'gkrellm.ds' with the following contents:

```
(if (is (application_name) "gkrellm") (undecorate (pin (below (skip_tasklist (skip_pager))))))
```

You might have to change the application name, depending on what name it comes up as (e.g., "Gkrellm" or something)...

---

### Post by x5452 on 2006-04-18
cool, thanks for that. What exactly does that DO though, I hate not understanding things I change.  I assume it will still save all the settings ect, and also allow for run on startup, correct?  But what/how does installing that and typing that do that, if you dont mind...  :mrgreen:

---

### Post by trent dillman on 2006-04-21
Devilspie does fun stuff to windows, like remove the wm decorations or pin to all desktops. I use it to put a terminal on my desktop....


... just be sure to add devilspie to your session startup (System > Preferences > Sessions).

---

