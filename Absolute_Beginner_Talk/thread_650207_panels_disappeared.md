---
title: "panels disappeared"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by iamclueless on 2007-12-26
ok

---

### Post by iamclueless on 2007-12-26
oooops posted without msg

im running xubuntu
ok my panels diappered..... wtf?  booted up and they are gone.  booted up a few more times, nothing

cant run panel manager. icon is there under settings but it doesnt do anything

can i reinstall this?

---

### Post by shareMenaPeace on 2007-12-26
you can try open a terminal and than type

killall gnome-panel
gnome-panel

(both maybe without the -)

Or login with failsafe and save and exit login normal ...?

---

### Post by Orfintain on 2007-12-27
Alt f1 is the default for show panel ... My panels freeze and become unusable sometimes, I just set a hot key for open terminal because there wasn't one for gusty (in the system preferences)

When they freeze there are vertical lines that run up and down them

---

### Post by ShelJ on 2007-12-27
> **shareMenaPeace said:**
> you can try open a terminal and than type

killall gnome-panel
gnome-panel

(both maybe without the -)

Or login with failsafe and save and exit login normal ...?

Tried both, did not work for me.  Any other sugg, please?

---

### Post by ShelJ on 2007-12-27
> **Orfintain said:**
> Alt f1 is the default for show panel ... My panels freeze and become unusable sometimes, I just set a hot key for open terminal because there wasn't one for gusty (in the system preferences)

When they freeze there are vertical lines that run up and down them

Alt[F1] opens website file:///usr/share/xfce4/doc/C/xfce4-panel.html#panel-manager, which doesn't help, since I can't get Panel Manager open either  ...  Could you poss elaborate on this, please?  Thanks.

---

### Post by Orfintain on 2007-12-27
If you go to system preferences >preferences> keyboard shortcuts

...is where i saw that, ---I really have no idea

---

### Post by ShelJ on 2007-12-27
Using Xubuntu?  try: 

```
  xfce4-panel 
```

worked for me after trying the other things on this post  ...

---

### Post by ShelJ on 2007-12-27
at least until I closed terminal  ...  Sorry.  But, I hope that it points you in the right direction.

---

### Post by ShelJ on 2007-12-27
Alright  ...  Follow previous instructions ```
xfce4-panel
```, but restart computer b4 closing terminal.  I tested restart thrice after this and panels remained.

---

