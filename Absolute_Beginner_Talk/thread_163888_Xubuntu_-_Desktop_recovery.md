---
title: "Xubuntu - Desktop recovery?"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by unbuntu on 2006-04-21
Hi,

I'm new to Xfce.  I ran nautilus under Xfce once, and now the desktop is messed up...

The desktop background is no longer "mouse in the moon", but the default ubuntu brown colour, and right click on the desktop doesn't bring up the menu anymore.  Anyone knows how can I get the Xfce desktop back?

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=unbuntu]Hi,

I'm new to Xfce.  I ran nautilus under Xfce once, and now the desktop is messed up...

The desktop background is no longer "mouse in the moon", but the default ubuntu brown colour, and right click on the desktop doesn't bring up the menu anymore.  Anyone knows how can I get the Xfce desktop back?[/QUOTE]

I had this same problem when I used XFCE. Put this in terminal while in XFCE:

> killall nautilus

Then reboot and it should be back to normal.

---

### Post by unbuntu on 2006-04-21
No, it doesn't work.  Still got the brown desktop background and right-clicking on desktop brings up nothing...

---

### Post by centered effect on 2006-04-21
try ```
xfdesktop&
``` in the terminal
then when you call up nautilus use: ```
nautilus --no-desktop
``` either in the terminal or as a icon

---

### Post by unbuntu on 2006-04-21
[QUOTE=centered effect]try ```
xfdesktop&
``` in the terminal
then when you call up nautilus use: ```
nautilus --no-desktop
``` either in the terminal or as a icon[/QUOTE]

It worked!  Thanks a lot.  I used nautilus because the default file manager in Xfce uses single click to open folders which I dont like.  I just upgraded to Xfce4.4beta, and the default file manager (thunar) uses double click too.  It feels nice to use Xfce

---

