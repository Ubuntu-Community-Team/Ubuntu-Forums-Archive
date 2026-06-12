---
title: "&quot;Super&quot;-key on Macbook Pro"
date: 2007-11-17
forum: Apple Intel Users
---

### Post by lv1001 on 2007-11-17
Hi,

To use compiz conveniently I would like to map the left apple key to "Super".
xev reports "Mode_Switch" for it now.
I tried "altwin:super_win" as an XkbOption in xorg.conf but that does not change anything. In /etc/X11/xkb/rules/xorg.lst no other options are mentioned to set a Super-key.
Did anyone manage to do this or do you change the compiz-keymaps accordingly?

Thanks
  LV

---

### Post by volanin on 2007-11-17
I am on a Macbook 3rd generation and both Apple Keys, or Window Keys if you use an external
keyboard, have always been mapped as Super. To say it better, Super is just the name that
GNOME gives to these keys.

Technically, you have to do nothing.
They are already Super!
:)

---

### Post by lv1001 on 2007-11-17
Yes, you are right. Sorry for this post.
I made a /etc/X11/Xmodmap when I installed linux on this machine to be able to use lv3 and the key left of the left key as delete.
I do not know why I did it then but I also changed the left Super key to Mode_switch.
I just removed that now...

Thanks
  LV

---

