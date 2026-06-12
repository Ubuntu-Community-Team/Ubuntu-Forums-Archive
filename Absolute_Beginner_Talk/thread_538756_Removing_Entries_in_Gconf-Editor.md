---
title: "Removing Entries in Gconf-Editor"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by willbur on 2007-08-30
Hi all

I notice many entries in gconf-editor (applications-system tools-configuration editor) that refer to software I previously removed from my Ubuntu Feisty installation. How can I ( or even should I?) remove these entries?

Many thanks to all in advance...

---

### Post by FleetAdmiral74 on 2007-08-30
If you don't know what you're doing, and its causing no problems at all, then I would think its perfectly safe to leave em.

You can always try, and just keep a backup of the file incase it crashes the system though.

---

### Post by willbur on 2007-08-31
Thanks, Fleetadmiral74. How would I go about doing this? There doesn't seem to be any way of removing entries from the gconf-editor....

Many thanks

---

### Post by asmoore82 on 2007-08-31
> **willbur said:**
> Hi all

I notice many entries in gconf-editor (applications-system tools-configuration editor) that refer to software I previously removed from my Ubuntu Feisty installation. How can I ( or even should I?) remove these entries?

Many thanks to all in advance...

In my experience, its best to leave them there because they take up very little space
and you may use them again someday.

if/when you backup your entire home directory and take it to another Linux install, you carry
all of your hidden files with personal settings with you... IMO this is *_feature_*.

if you really want the entries gone you can follow these steps.

1. using apt/Synaptic, **purge** the package that created them, just incase their schemas are still installed
2. login to a failsafe terminal, GNOME and the GConf Daemon cannot be running
3. delete the entries from $HOME/.gconf/ ...

This procedure is rarely neccessary but I use it when swithing between breeds
and builds of desktop effects. I.E. I run this from a failsafe terminal ...
```
~ $ rm -rf .gconf/apps/compiz
```

---

### Post by willbur on 2007-08-31
Thanks, asmoore82.

 When you say 'log in to a failsafe terminal' do you mean by using, say, ctrl-alt-f1? How do I stop GNOME and the GConf daemon from running, please?

Regards

---

### Post by asmoore82 on 2007-08-31
> **willbur said:**
> Thanks, asmoore82.

 When you say 'log in to a failsafe terminal' do you mean by using, say, ctrl-alt-f1? How do I stop GNOME and the GConf daemon from running, please?

Regards

Logout to the gdm greeter screen and then 
either ctrl-alt-f1
-OR-
just pick "failsafe terminal" as the **session type** from the gdm greeter and log back in

---

### Post by willbur on 2007-08-31
Thanks - I'll give it a try!

---

### Post by willbur on 2007-08-31
Many thanks, asmoore82. That removed all the values from the gconf-editor right pane for the previously uninstalled apps in question.

How do I remove their Gconf-editor entries in the tree view on the left under 'apps' and 'schemas-apps'?

Thanks again - your help is much appreciated. I'm still at the  steep bit of the Ubuntu learning curve ;-)

---

### Post by willbur on 2007-08-31
Any ideas, anyone?

---

### Post by noynac on 2007-08-31
I've never used it, but there is a utility called GConf Cleaner:

*GConf Cleaner is a tool to clean up the unknown/invalid gconf keys that still sitting down on your gconf database.*

[http://www.getdeb.net/app.php?name=GConf+Cleaner](http://www.getdeb.net/app.php?name=GConf+Cleaner)

EDIT: I tried this utility, and it is overly aggressive in removing entries. I'd avoid it.

---

### Post by willbur on 2007-09-01
OK - thanks anyway. Surely I'd be able to 'sudo rm' these folders if someone can please tell me where they are? Not in /home/.gconf - I've looked...

---

