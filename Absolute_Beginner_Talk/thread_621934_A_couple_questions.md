---
title: "A couple questions"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by l33tc0d34 on 2007-11-24
I have installed gutsy & everything was fine for a few days.  I don't know what happened but last night I lost internet access.  I found that ifconfig only showed the loopback interface (lo).  Reviewing /etc/network/interfaces I found that none of my network cards were defined (eth0 & wireless).  I added entries & was able to get wired & wireless working again.

The network-manager applet no longer works though :-( ... If I click on it, it just says "Manual Configuration" - it doesn't show me the wireless networks that are in range, etc like it used to.  I uninstalled & reinstalled network-manager & gnome-network-manager hoping that would fix the problem but it didn't...  How can I fix network-manager?

Also, if I create a custom app launcher on the panel it always disappears after a reboot or logoff...  why does it do this & how can I prevent it from happening?

Thank you.

---

### Post by kevindubrow on 2007-11-24
Do you think you could tell us what wireless card you are using?

And sorry, I have no clue about the app launchers. Do they disappear even if you make Ubuntu create one (going into the applications menu, right clicking on a program, and clicking "add this launcher to panel)?

---

### Post by l33tc0d34 on 2007-11-24
Regarding the app launcher...

If I right click an item in the menu & select "add to panel" - the launcher never disappears.

If I right click the panel, add to panel -> custom application launcher - those launchers disappear after a reboot or logoff.  I'm just trying to add launchers to a couple of scripts that I have - the launchers work fine after I add them, but they're always gone after reboot / logoff....  and I don't know why!!

Regarding the wireless card, I'm really not sure what the model is... it uses the ath_pci driver & works just fine if I do an "ifup ath0"... that would be fine if this weren't a laptop & I didn't take it to a number of places that use wep / wpa.  I don't want to have to edit etc/network/interfaces every time i need to connect to a new wlan.

---

### Post by sailor2001 on 2007-11-24
system/sessions  add what you want for start-up

---

### Post by l33tc0d34 on 2007-11-24
I don't want it to start up when I log in..

I just want to make a launcher for an app / script that doesn't appear in the menu.

Can someone else try to create a custom launcher, reboot & see if it is gone?  I'm starting to think I'm sounding crazy.

---

