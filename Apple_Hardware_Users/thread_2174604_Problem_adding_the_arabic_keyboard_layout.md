---
title: "Problem adding the arabic keyboard layout"
date: 2013-09-15
forum: Apple Hardware Users
---

### Post by yousufinternet on 2013-09-15
Hi every one

I have recently installed Ubuntu on my Apple MacBook Pro 9,2, everything works fine except for one problem, when I try to add the Arabic keyboard layout I keep getting this message, I don't get this message when I add other layouts such as Albanian for example, it only appears with Arabic :( , it might be because I have edited the keyboard layout manually at /usr/share/X11/xkb/symbols/ara but I still get the same problem even after restoring the original layout.. 
> 
 Error activating XKB configuration.
There can be various reasons for that.

If you report this situation as a bug, include the results of
• xprop -root | grep XKB
• gsettings get org.gnome.libgnomekbd.keyboard model
• gsettings get org.gnome.libgnomekbd.keyboard layouts
• gsettings get org.gnome.libgnomekbd.keyboard options 

any suggestions would be useful.. 

thanks in advance

---

