---
title: "GDM theme executed from command line???"
date: 2010-03-07
forum: Art &amp; Design
---

### Post by chips24 on 2010-03-07
i just recently installed ubuntu 9.10 on my friends computer, he wanted a windows seven theme, so i got everything to look like winodws7. however i could not change the GDM theme. i was looking at other posts and found some codes for the terminal. i do not have a computer anymore, so i cant try this. 

does the command...

gksudo -u gdm dbus-launch gnome-appearance-properties

open the gdm theme manager???

---

### Post by Flimm on 2010-03-08
Ubuntu 9.10 doesn't use GDM themes any more, try looking for Xsplash themes instead. ([Epidermis](http://epidermis.tuxfamily.org) supports them.)

---

### Post by mcduck on 2010-03-09
> **chips24 said:**
> i just recently installed ubuntu 9.10 on my friends computer, he wanted a windows seven theme, so i got everything to look like winodws7. however i could not change the GDM theme. i was looking at other posts and found some codes for the terminal. i do not have a computer anymore, so i cant try this. 

does the command...

gksudo -u gdm dbus-launch gnome-appearance-properties

open the gdm theme manager???

Like above poster said, Ubuntu 9.10 and later don't use that kind of GDM themes any more. But the command you posted *does* allow you to customize your GDM, it opens the Appearance preferences-window as user "gdm" so you'll be able to set the theme, background & fonts of the login screen.

You'll see two accessibility icons appear in the notification area when you run the command, one will disappear on it's own when you log out & back, while the other one you can remove by going to System/Preferences/Keyboard, and disabling the "Accessibility features can be toggled with keyboard shortcuts"-option on the Accessibility tab.

---

