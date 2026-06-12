---
title: "Menubar / status bar disappeared"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by gos on 2008-02-05
After the last reboot the status and menu bars on my desktop  have diappeared.  I´m using a pretty standard setup 7.10 with Gnome.  When I log on the bars flash for a few seconds and then disappear. Someone on the forum suggested deleting .gnome2 folder (under /home/user) which I did but after that nothing shows up on the desktop at all (icons showd up before).  Any suggestions appreciated - I can't use the system until I get this fixed.

best regards, gos

---

### Post by Ub1476 on 2008-02-05
First take the folder you deleted back from trash. Then try to run this command (and logout):

```
sudo apt-get install ubuntu-desktop --reinstall
``` 

If nothing has changed run gnome-panels with this:

```
gnome-panel
```

I suppose you know you can add applets by right clicking>add to panel.

---

### Post by SunnyRabbiera on 2008-02-05
I have had bugs like this myself, its a major pain in gutsy.

---

### Post by gos on 2008-02-06
Thanks for the advice - I deleted the dir in command line so I guess it´s forever gone?  I tried apt-get install ubuntu-desktop --reinstall but it doesn´t find it - it's not in the sources list??
 I booted up in recovery mode to enter these commands.  Also gnome-panel command  - what parameter should I set for this.  Sorry for these questions - I´m a linux noob.

best regards, gos

---

### Post by gos on 2008-02-06
Does anyone know which repository ubuntu-desktop needs?  There are no lines commented out in my sources.list.  Is there any other way to get back my status and menu bars - do you know ?

best regards gos

---

### Post by Ub1476 on 2008-02-17
Make sure the sources is enabled in Software Sources.

You can also try to run:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg --configure -a
```

Then try to reinstall ubuntu-desktop again (you can search for it in Synaptic as well).

If none of this works, I have no clue, sorry.

---

