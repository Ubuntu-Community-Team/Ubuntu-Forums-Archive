---
title: "Conky control menu disappeared in Voyager (Xubuntu 12.10)"
date: 2013-09-03
forum: Any Other OS
---

### Post by squiddy2 on 2013-09-03
I just installed the Voyager distribution on Ubuntu 12.10 and one of the things I immediately loved about it was the Conky control menu that popped up when I right-clicked anywhere on the desktop. But within half an hour of using Voyager, that menu disappeared!:mad: Now when I right-click the pop-up menu is similar to the one on the panel that displays the application list, log out, etc. I can't figure out how to get back the original menu or even access conky control some other way. Has anyone ever experienced this? Any suggestions?

---

### Post by Toz on 2013-09-03
*Moving to **Other OS/Distro Support**.*

I don't use Voyager, but this type of behaviour (menus changing on desktop) happen in Xfce when you enable/disable displaying icons on the desktop. In other words, if you disable icon display on the desktop, you will see the applications menu on right-click. If you enable icons, you see a different menu of which the applications menu is a submenu (it is possible that the link to the conky manager is in this menu). Desktop icons can be enabled/disabled via Settings Manager -> Desktop -> Icons tab.

It can also happen if you replace xfwm4 (the Xfce window manager) with another window manager. To check if xfwm4 is running, go to Settings Manager -> Session and Startup -> Session tab and see if its listed.

Does conky manager show up anywhere in the applications menu? Maybe under Accessories or System?

---

### Post by squiddy2 on 2013-09-03
Thanks so much! You're right, the problem was that I had disabled the icons on my desktop. Can't believe that I went through so much head-scratching over that one! You're a lifesaver :)

---

