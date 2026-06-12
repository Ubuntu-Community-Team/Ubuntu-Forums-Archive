---
title: "[SOLVED] HELP No Panels!!!!"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by SPRL on 2007-07-26
Noob ops...please help... I was turning off desktop efects and the screen flickered and poof no panels. All I have is  my background and when I reboot my home directory pops up (how I managed to get here). I tried Alt F2 and nothing happens...can someone please help me get them back ](*,)

---

### Post by tbroderick on 2007-07-27
Try deleting your ~/.gnome2 folder. It will reset GNOME to the default config.

---

### Post by AceofSpades19 on 2007-07-27
press ctrl-alt-f1 and login and type rm -r .gnome2f

---

### Post by SPRL on 2007-07-27
Thanks for all the help, I was able to get them back this way. (don't know if its right but it worked)
Ok to begin nothing was working, no icons, no alt f2, no ctrl alt f1 just my background after I rebooted a few times. I was able to right click for the background and whent to online help, from there to the forum.
So this is how I fixed it, ctrl-alt-backspace to get to login, clicked sessions (panel bottom left) and chose gnome-failsafe, and loged in. Panels were there, went to terminal and typed... 

Quote:
killall gnome-panel

Then rebooted.
Alls well once again.

---

