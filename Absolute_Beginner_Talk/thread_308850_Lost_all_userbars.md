---
title: "Lost all userbars"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-11-28
Hi guys,
Haven't been here for a while since i've been dead busy IRL, but today while I was mucking around I accidently removed the top bar and changed settings for the bottom...
Is there anyway to reset the GUI back to the original without reinstall ubuntu?

- Josh

---

### Post by xpod on 2006-11-28
You can add or remove panels by right clicking them....you can also add lots of little gizmos too with the "add to panel" feature

---

### Post by taurus on 2006-11-28
You can delete ~/.gnome2...

```
rm -rf ~/.gnome2
```

---

### Post by Josh1 on 2006-11-28
> **xpod said:**
> You can add or remove panels by right clicking them....you can also add lots of little gizmos too with the "add to panel" feature

That's what I was doing, but I can't get it the way ubuntu had. :(

> **taurus said:**
> You can delete ~/.gnome2...

```
rm -rf ~/.gnome2
```

And remove GNOME? Might as well use KDE then lol.

---

### Post by taurus on 2006-11-28
> **Josh1 said:**
> That's what I was doing, but I can't get it the way ubuntu had. :(



And remove GNOME? Might as well use KDE then lol.
That doesn't mean remove Gnome from your machine!!!  Just the settings for your account...  The next time you log back into Gnome, it will reset everything back to defaults.

---

### Post by Josh1 on 2006-11-28
> **taurus said:**
> That doesn't mean remove Gnome from your machine!!!  Just the settings for your account...  The next time you log back into Gnome, it will reset everything back to defaults.

Ahh my bad, cheers.

---

### Post by Josh1 on 2006-11-28
Ok that didn't work, typed it in terminal, relogged, didn't work, so i then wrote it in the main terminal (CTRL+F1) then relogged and that didn't work, logged out then did it in Terminal1 then relogged in, didn't work, wrote it in Terminal1 then rebooted, didn't work..

Any ideas?

---

### Post by taurus on 2006-11-28
Boot into recovery mode and at the prompt, run

```
rm -rf /home/josh1/.gnome  /home/josh1/.gnome2  /home/josh1/.gnome2_private
(assuming josh1 is your login name...)
```
Reboot and see what happens if you log in as josh1 again.

---

