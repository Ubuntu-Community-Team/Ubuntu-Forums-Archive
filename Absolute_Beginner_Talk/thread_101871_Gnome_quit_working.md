---
title: "Gnome quit working"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by sterrac on 2005-12-10
I have both the Ubuntu desktop and the Kubuntu desktop on my system. I made some changes using KControl to KDE; afterwards, Gnome refused to start. It would show me the splash screen, try to load the panels at the top and bottom, give me the gong of death(sound), then try again. It will never quit trying to start and will not tell me anything about the error. 

Has anyone had this experience and know of a fix? I have tried reinstalling both gnome and ubuntu desktop, and backtracing my steps through the changes I made to KDE to no avail. Any help would be appreciated, I am starting to look dumb in front of my kids.

Shane

---

### Post by kairu0 on 2005-12-10
Does this happen with all of your user accounts?

---

### Post by teaker1s on 2005-12-10
terminal login and 
'dmesg' 
post output
also delete 
iceauthority file in home folder as it may be corrupt

---

### Post by sterrac on 2005-12-11
It only bombs on my profile, works on two other profiles just fine. I logged into a failsafe terminal and dmesg, I think I did this right, the output below is just a sample, but it continues in the same fashion for 2 pages.

[48565.986566] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[48565.995446] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[48565.995464] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[48566.296593] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).

sorry it took so long to reply.

Shane

---

### Post by infoseeker on 2005-12-11
Try the following :
[http://www.ubuntuforums.org/showthread.php?t=101559](http://www.ubuntuforums.org/showthread.php?t=101559)

---

### Post by sterrac on 2005-12-11
Thanks, I followed the link and removed the gtk-qt and gnome now works. I appreciate all help recieved.

Shane

---

