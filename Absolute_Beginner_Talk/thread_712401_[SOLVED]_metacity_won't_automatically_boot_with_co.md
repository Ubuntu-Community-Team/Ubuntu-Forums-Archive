---
title: "[SOLVED] metacity won't automatically boot with compiz turned on"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by meanburrito920 on 2008-03-01
I recently (5 min ago) decided to switch back to metacity from emerald. However, I wanted to keep my other compiz effects. I went into the Desktop Effects Settings app and changed the default manager to metacity. However it still boots into emerald for some reason, even though nothing is telling it to do so. Why would it do this and how can I get metacity back without losing my other desktop effects?

---

### Post by rainwalker on 2008-03-01
You could try uninstalling Emerald; I think as long as it is installed Compiz tries to use it (probably a bug?)

---

### Post by meanburrito920 on 2008-03-01
but since I like to switch around themes a lot I dont want to have to continuously uninstall and reinstall it...

---

### Post by Oldsoldier2003 on 2008-03-01
> **meanburrito920 said:**
> but since I like to switch around themes a lot I dont want to have to continuously uninstall and reinstall it...
turn off desktop effects, then in a terminal do ```
metacity --replace
``` save your session and restart X

metacity doesn't do desktop effects you need emerald for those. So if you want to pop back and forth you'll need to disable the visual effects in Appearance preference

---

### Post by rainwalker on 2008-03-01
Metacity can be used with the visual effects. After all, it's the default window manager; You have to install Emerald.

---

### Post by Oldsoldier2003 on 2008-03-01
> **rainwalker said:**
> Metacity can be used with the visual effects. After all, it's the default window manager; You have to install Emerald.
Without emerald installed  you can't even enable the visual effects. thats why we told him to go to appearance preferences and disable the visual effects. before removing emerald. if you want the compiz effects you **have** to use emerald, metacity doesn't do them.

---

