---
title: "Can't press Super L + other key"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by tL0z on 2007-06-07
I'm trying to add some keyboard shortcuts such as Super L + D but I can't. The "acelerator detector" stops right when I press the Super L key.

---

### Post by steeleyuk on 2007-06-07
Ubuntu generally uses CTRL + ALT + <insert letter here> rather than SUPER keys for shortcuts. My copy of Ubuntu does exactly the same thing though I can't understand why the devs didn't allow SUPER + <insert letter here>. Maybe it was an oversight.

To summarise, I have the same problem...

---

### Post by tL0z on 2007-06-09
Anyone?

---

### Post by tL0z on 2007-06-16
No help? :(

---

### Post by AnonChap on 2008-01-05
Bumping this, as it still applies to Ubuntu 7.10

Well, I think this is Super + Gay!

On Fedora, I could use Super + z and Super + x to switch between workspaces. That was using KDE though. Perhaps this is an issues with gnome? Anyway, super is a nice key to use in combo with other keys, because it has no default maps afaik. (I know amarok uses Super for play/stop/next etc)

---

### Post by p_quarles on 2008-01-05
Your suspicion is correct. Gnome does not allow the super keys to be used as modifiers. KDE does.

---

### Post by AnonChap on 2008-01-05
/me installs KDE

---

### Post by matthodge on 2008-02-07
Here is the solution : 

1) Goto System > Preferences > Keyboard
2) Goto "Layout Options" tab.
3) Expand "Alt/Win Behavior".
4) Put the dot on "Super is mapped to the Win-keys (default)".
5) Press close.
6) Goto System > Preferences > Keyboard Shortcuts.
7) Map your WinKey + Whatever combos.

It should come up as "Mod4+ *KEY*"

---

### Post by argie on 2008-02-07
> **matthodge said:**
> Here is the solution : 

1) Goto System > Preferences > Keyboard
2) Goto "Layout Options" tab.
3) Expand "Alt/Win Behavior".
4) Put the dot on "Super is mapped to the Win-keys (default)".
5) Press close.
6) Goto System > Preferences > Keyboard Shortcuts.
7) Map your WinKey + Whatever combos.

It should come up as "Mod4+ *KEY*"

Wow thank you sir! I'd switched to making Compiz handle all those shortcuts. This helps lots.

---

### Post by Copter on 2008-05-15
Thanks matthodge. It did the trick.

---

### Post by alexmclaren on 2008-07-04
similar problem, only i don't know WHERE the super key is on my keyboard or what it should look like to begin to have the problem, but it cuts out the possibility for some shortcut keys ... is the issue with the Win Key substitution above that windows keyboards do not have this key?

---

