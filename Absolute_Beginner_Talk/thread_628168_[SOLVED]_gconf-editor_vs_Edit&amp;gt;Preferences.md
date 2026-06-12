---
title: "[SOLVED] gconf-editor vs Edit&amp;gt;Preferences??"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Bigbird999 on 2007-11-30
A couple examples. 

 I can set the folder default view as list_view by editing gconf-editor apps/nautilus/preferences, but it doesn't work and the next time I open a folder in nautilus I get the icon_view.  But if I open nautilus and Edit>Preferences and select my defaut view as list it works. 

 In gconf-editor there are a bunch of preferences for power management in gnome power manager (way more than available in the power manager applet preferences) .  Changing them here has no  effect that I can detect on the power manager handles/manages screen shutdown timeots,  etc.  The only way I can change how powermanager works is by editing the prefs in the applet.

So what does gconf-editor do?  Am I not using it properly? 

BB

---

### Post by jken146 on 2007-12-01
gconf-editor is useful for doing things you can't do in the menus.  For example, you can turn off the desktop, or turn off the wallpaper, as well as choosing whether or not to display the home folder icon, the trash icon, icons for mounted drives (those in /media) etc.

---

### Post by jaybombalous on 2007-12-01
make sure u are running gconf-editor as your user account and not the root account.


settings that u want to affect your user desktop must be made with out using sudo. I am almost positive that is your problem.

---

### Post by Bigbird999 on 2007-12-01
>  make sure u are running gconf-editor as your user account and not the root account.


settings that u want to affect your user desktop must be made with out using sudo. I am almost positive that is your problem.


YUP.  I was using sudo because.....well......you have to use it to change anything, right!!!!   Makes sense now that I think about it..  

Thanks

I'll mark it solved

---

### Post by jaybombalous on 2007-12-01
you're welcome, just remember there is a difference and a reason for sudo, its not the 'go' all command though, as u now realize.

---

