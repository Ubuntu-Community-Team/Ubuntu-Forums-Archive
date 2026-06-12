---
title: "Permissions for icons"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by drfox on 2006-04-29
I downloaded the orange firefox icon and tried to install it in the icon directory, but that is owned by root. I tried installing a new desktop theme and saving it to the theme directory. Same problem.

What are other people doing with these permission problems? I have heard there is less of a problem with KDE. Surely Gnome has a workaround.

Thanks.  Larry

---

### Post by testube_babies on 2006-04-29
You should just be able to drag the icon package or theme package into the window when you open System -> Preferences -> Theme.  This installs the icons/theme so that you are the owner and have permissions to edit them.

---

### Post by Gannin on 2006-04-29
This isn't Gnome or KDE specific, per se'.  It's simply a matter of permissions.  Where are you trying to install the new icons?  /usr/share/pixmaps?  /usr/share/icons?  Either way, you'll need to use the sudo command, such as, sudo mv iconfile.png /usr/share/wherever.

You can do the same thing with the theme folder you're trying to use, moving it to /usr/share/themes, but if you're the only person using your computer, or if you're all using the same account, it would be better to put it in ~/.themes.

---

