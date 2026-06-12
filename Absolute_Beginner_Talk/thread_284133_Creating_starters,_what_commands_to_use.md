---
title: "Creating starters, what commands to use?"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Nuibkulnatsu on 2006-10-25
I'm trying to configure my gdesklet-starterbar and having difficulties creating starters. I would for example like a starter to logout, like the one in the ordinary menu, what command should I use? The same goes for the starter of the terminal. I don't get much help looking at the existing starters as they don't have any properties.

Is there a way to use emblems in the starterbar? Would be really nice to distinguish a shortcut to a directory from another one, sure I can use different icons but I like the ones I have.

---

### Post by crossedout on 2006-10-25
gnome-terminal is the Command to use for a Terminal starter.

-Xout

---

### Post by Nuibkulnatsu on 2006-10-26
Excellent!, thank you.

Im still looking for the command to logout though, I could perhaps use the reboot or poweroff command but i really like the gnomescreen which gives the option to change users etc..

---

### Post by TitusDalwards on 2006-10-26
```
killall x-session-manager
```

with this command you return to GDM screen and you are able to change user.

---

