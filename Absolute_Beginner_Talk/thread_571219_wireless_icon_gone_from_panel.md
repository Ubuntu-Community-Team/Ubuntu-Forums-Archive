---
title: "wireless icon gone from panel"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-10-09
I can't get the wireless icon back on to the panel. I have tried network monitor icon but thats not what i'm after. Im after one were if you left click it shows the wireless connections available and gives option of creating a new wireless connection etc.  Any help

---

### Post by dcstar on 2007-10-09
> **Dark-Angel said:**
> I can't get the wireless icon back on to the panel. I have tried network monitor icon but thats not what i'm after. Im after one were if you left click it shows the wireless connections available and gives option of creating a new wireless connection etc.  Any help

Try reinstalling the gnome-netstatus-applet & wireless-tools packages.

---

### Post by RomeReactor on 2007-10-09
Hi. Before you try re-installing those packages: have you tried restarting your display (CTRL+ALT+BACKSPACE) or rebooting? if not, try this first: press ALT+F2, and enter the following:
```
nm-applet --sm-disable
```
and see if Network Manager shows up now.

Also it could be that the **Notification Area** applet was removed somehow; to add it, right-click on an empty part of the top panel and select "Add to panel...". Form the applets shown, scroll to the bottom and choose "Notification Area". Now see if Network Manager shows up.

---

### Post by Dark-Angel on 2007-10-09
> **RomeReactor said:**
> Hi. Before you try re-installing those packages: have you tried restarting your display (CTRL+ALT+BACKSPACE) or rebooting? if not, try this first: press ALT+F2, and enter the following:
```
nm-applet --sm-disable
```
and see if Network Manager shows up now.

Also it could be that the **Notification Area** applet was removed somehow; to add it, right-click on an empty part of the top panel and select "Add to panel...". Form the applets shown, scroll to the bottom and choose "Notification Area". Now see if Network Manager shows up.

I tried that  ```
nm-applet --sm-disable
``` and it came up saying it couldn't find it.

---

### Post by RomeReactor on 2007-10-09
Search for **network-manager-gnome** in Synaptic and see if it's marked as a broken package; you'll probably need to reinstall it.

---

### Post by Dark-Angel on 2007-10-09
it has a white box next to it. if i have to reinstall is there a way with out internet as i would have to move it to get wired to get it again so i can try to get the wire less working

---

### Post by scrooge_74 on 2007-10-09
you could download the .deb package in another PC and then installed in your. But still try to install it, usually the package is there unless you tell the system to purge package that were remove.

Next time you loose the icon, open a terminal and just type nm-applet, it will come on, then log out (without closing the terminal) and then log back in

---

### Post by RomeReactor on 2007-10-09
If it has a white (empty) box beside it, then it's not installed. If you had it installed before, there's a chance the .deb package is still there. Try marking it for installation and click Apply.

If you don't have the package anymore, your best option, in my opinion, is to connect this computer to the internet and then install network-manager-gnome, so Synaptic also downloads and installs all of its dependencies.

Did you have it installed previously?

---

### Post by Dark-Angel on 2007-10-09
i did but i just tried doing reinstall and tries to connect to internet so I guess i'll just have to move it then and connect it up wired

---

### Post by scrooge_74 on 2007-10-09
If you still have Live CD, you can tell synaptic to use it as repository, the app is in the CD since it gets install by default when you use the CD

---

