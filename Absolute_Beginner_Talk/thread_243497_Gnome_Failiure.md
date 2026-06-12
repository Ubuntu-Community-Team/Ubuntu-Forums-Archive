---
title: "Gnome Failiure"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Abhinav Sharma on 2006-08-25
I have Kubuntu installed on my computer along with the latest Gnome and Dapper. I prefer working on Gnome. When I last used Gnome, I accidently changed the theme and once changed, I was unable to access the Theme manager as that button was grayed out. Ever since , when I start my system with Gnome, the Gnome loading icons show up but I'm left with a blank screen.

Is there any way I can restore Gnome back to original settings using KDE or a shell?

---

### Post by Perfect Storm on 2006-08-25
You could try removing the theme from the theme folder.

Or try starting gnome theme selector up in KDE (I don't know if it works, but worth a try):

```
gnome-theme-manager
```

By the way which theme did the mess up? Are you sure it's the theme that did it?

---

### Post by tomBorgia on 2006-08-25
Hiya, you could try removing the .gnome folder (this stores all your gnome settings)... even better just rename it. When you log back into gnome it should recreate it... 

From the command line: 

tom@tom-ubuntu-desktop:~$cd /home/(username)
tom@tom-ubuntu-desktop:~$sudo mv -rdf .gnome .gnome-bakup
tom@tom-ubuntu-desktop:~$startx

---

### Post by Abhinav Sharma on 2006-08-25
I tried gnome-desktop-manager from KDE to revert to the default theme and everything works fine now. Thanks for the help.

---

