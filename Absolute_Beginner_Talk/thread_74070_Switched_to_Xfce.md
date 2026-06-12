---
title: "Switched to Xfce?"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by Dayylin on 2005-10-10
Booted my system up today and I have a new desktop lol. How do I get back to gnome from Xfce?

---

### Post by aysiu on 2005-10-10
Log out.
Under **Session**, pick **Gnome**.
Log back in.

---

### Post by Dayylin on 2005-10-10
Only option it gave for gnome was failsafe and it wasn't failsafe lol. No gnome can be found. I haven't removed anything so I am kinda confused on what I did to it.

Brian

---

### Post by aysiu on 2005-10-10
When you open up Synaptic in XFCE, do you see Gnome in there?

---

### Post by Dayylin on 2005-10-10
Hmmm apparently I no longer have synaptic. This is strange

---

### Post by aysiu on 2005-10-10
[QUOTE=Dayylin]Hmmm apparently I no longer have synaptic. This is strange[/QUOTE] Can you get Synaptic back by typing this in a terminal? ```
sudo apt-get install synaptic
```

---

### Post by Dayylin on 2005-10-10
It appeared to apt-get ok but still not showing synaptic anywhere.

---

### Post by racecat on 2005-10-10
[QUOTE=Dayylin]It appeared to apt-get ok but still not showing synaptic anywhere.[/QUOTE]

Synaptic doesn't show up on the Xfce menus. I add it to the Xfce panel launcher. Use the command line:

gksudo synaptic

Hope this helps
Bill

---

### Post by aysiu on 2005-10-10
Synaptic may not show up in a menu, but if it's installed, you can just open up the **Run...** command and type ```
gksudo synaptic
```

---

### Post by Dayylin on 2005-10-10
Ok cool. Got synaptic open finally lol. If I uninstall the xfce options, will that restore gnome?

---

### Post by stuporglue on 2005-10-10
Reinstall Gnome first, so you're not left with no desktop at all -- probably not fun. :-) 

If you want everything back "how it was" install ubuntu-dekstop and it'll re-install everything that comes with Ubuntu by default. Use synaptic or in a terminal

"sudo apt-get install ubuntu-desktop"

---

### Post by aysiu on 2005-10-10
[QUOTE=Dayylin]Ok cool. Got synaptic open finally lol. If I uninstall the xfce options, will that restore gnome?[/QUOTE] No. Uninstalling XFCE will just uninstall XFCE. What happens when you search for Gnome? Or the Ubuntu-desktop package?

---

### Post by Dayylin on 2005-10-10
Seems like most of my gnome stuff was uninstalled for lack of a better word. Checking them back in.

---

