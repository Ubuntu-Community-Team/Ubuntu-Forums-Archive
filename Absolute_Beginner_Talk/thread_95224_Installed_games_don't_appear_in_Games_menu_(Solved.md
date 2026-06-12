---
title: "Installed games don't appear in Games menu (Solved)"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Granduke on 2005-11-26
I've must have installed over 20 games with Synaptic Package Manager only 2 or 3 appear under the Applications - Games menu.  Where did the rest go? Am I missing a step?
All my installations thru 'Add Applications' do end up in the menus.  But installations thru Synaptic rarely do.

---

### Post by aysiu on 2005-11-26
Add Applications, as far as I know, is just a simpler version of Synaptic Package Manager. I think it depends on the game you're installing, not the application you're installing it with.

Just to be sure, though, try running this command ```
killall gnome-panel
``` Did a menu item appear? If not, you may have to add it manually...

---

### Post by cdhotfire on 2005-11-26
Do what aysiu said, but if that doesn't work, these games might not come with a menu selection. You can always go to Synaptic and check what things it installed (select package, right click, select properties, Installed Files tab, check for the name of the program in /etc/ or /usr/bin/), after you have name try to run in terminal. Then just use smeg to add it to menu.:smile:

---

### Post by aysiu on 2005-11-26
[QUOTE=cdhotfire]Then just use smeg to add it to menu.:smile:[/QUOTE] In Breezy, SMEG may be called Applications Menu Editor.

---

### Post by doclivingston on 2005-11-26
As others mentioned, the game may not have a menu item set up for it. If it doesn't, it's worth filing a bug about, so that someone will make sure it has one in Dapper.

---

### Post by Granduke on 2005-11-26
Thanks guys. The games were being installed without menu selections.  I'm adding their entries with SMEG.
xarchon- I haven't played Archon since my Apple II days. :smile:

---

### Post by cdhotfire on 2005-11-26
[quote=aysiu]In Breezy, SMEG may be called Applications Menu Editor.[/quote]

good call.8-)

---

