---
title: "Debian menu and Ctrl+Alt+Del shortcut not working"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-02-07
Hi,

I've used Automatix2 to install some common stuff on Ubuntu. However at least 2 things are not working:

1) Debian menu: I've installed it through Automatix2 and restarted the computer but the Debian menu doesn't show up. I've then tried zo enable it from System->Preferences->Menu layout but I cannot put a mark on the checkbox...

2) Ctrl+Alt+Delete shortcut to System monitor: I've also installed this though Automatix2 but the shortcut doesn't work. I've looked in the configuration editor in Gnome under Apps->Metacity->Global_keybindings and Ctrl+Alt+Delete is set as run_command_9. In Apps->Metacity->keybindings_commands the comand_9 is set to gnome-system-monitor so the shortcut is correctly installed and it should work but it doesn't. Nothing happens when I press Ctrl+Alt+Del

Any clue about these 2 issues?

Thanks

---

### Post by kilou on 2007-02-07
up

---

### Post by raul_ on 2007-02-07
You have to mark the folders *under* the Debian menu in the Menu Layout. 

About the second issue, are you using Beryl?

---

### Post by kilou on 2007-02-08
Thanks for your reply raul_. I cannot check the Debian menu box in menu layout for some reasons. When I click on it it remains blank :confused: This not only happens for Debian menu in fact, I cannot check any blank boxes......but I can remove the mark of any already loaded menu items.......weird!

Yes I use Beryl. However I couldn't find any shortcut attributed to Ctrl+Alt+Delete....and when I press these keys nothing happens. Do you know more on this topic????

Thanks

EDIT: just found how to solve the problem with Ctrl+Alt+Delete and Beryl: I had to define this shortcut in Beryl under command and bind it to Gnome-system-monitor. However I still can't manage to understand why I cannot activate Debian menu in the menu layout.

---

