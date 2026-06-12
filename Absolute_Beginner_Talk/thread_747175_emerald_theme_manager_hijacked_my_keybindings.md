---
title: "emerald theme manager hijacked my keybindings"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by gsub on 2008-04-06
Hi, all.

I had assigned using gconf-editor the key combination <Mod4>+E (windows key + E) to launch the text editor. Upon installing emerald theme manager, this combination now switches workspaces. However, in gconf-editor, it is still listed as launching text editor.

Anyone know where emerald stores its keybinding information?

Thanks in advance.

---

### Post by Moop on 2008-04-06
I don't think that's a Emerald key binding. It's probably a compiz key binding. You can install compizconfig-settings-manager to check the compiz settings.

---

### Post by autocrosser on 2008-04-06
Yes, that is a Compiz setting--use settings-manager to work with your bindings. I would also install fusion-icon (sudo apt-get fusion-icon   if you are using Gutsy) to have more control over Compiz.

---

### Post by gsub on 2008-04-06
you guys are right... it is a compiz settings problem. i first removed both emerald and compiz, then reinstalled just compiz. when i switch my desktop settings to "Normal", the <mod4>+e gets hijacked

but, in the compiz-config-settings manager, mod4+e is still defined as launching gedit, and there doesnt seem to be a place where switching workspaces is defined.

any thoughts, people? i've attached screenshots, in case i wasn't clear in the few lines above.

---

### Post by autocrosser on 2008-04-06
Sounds like you need to goto:  [http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)  & ask a few questions....

---

### Post by gsub on 2008-04-06
well, nevermind... i found it...

---

