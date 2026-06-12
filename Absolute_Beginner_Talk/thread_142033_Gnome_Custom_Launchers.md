---
title: "Gnome Custom Launchers"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-03-09
is there a way to have a prompt come up to put in options so that when i open a program i can change the variables before it runs?

---

### Post by aysiu on 2006-03-09
You can modify the launcher command.

Right-click on the Gnome menu and select "edit menu."

Then find the application launcher and modify the command.

For example, if the command for "Take a Screenshot" is ```
gnome-screenshot
``` but you actually want it to delay, then change it to ```
gnome-screenshot --delay 5
```

---

### Post by obey43 on 2006-03-09
right but is there a way to make it prompt you with a box for the options when you click it,

because sometimes i want it to open with the interface -eth0 and sometimes -wlan0.

or -colortheme 3  and -colortheme 6  with out making seperate launchers?

---

### Post by aysiu on 2006-03-09
[QUOTE=obey43]right but is there a way to make it prompt you with a box for the options when you click it,

because sometimes i want it to open with the interface -eth0 and sometimes -wlan0.

or -colortheme 3  and -colortheme 6  with out making seperate launchers?[/QUOTE] I don't know. Creating a prompt would probably require some programming, which is probably more trouble than making separate launchers.

If you're worried about the space launchers take up, you could also just create keyboard shortcuts for those commands.

---

### Post by lambros on 2006-03-09
Have a look at the "zenity" command.  Example:

```
zenity --list --title "MyLauncher" --text "Which interface to you want to open?" --column "Interfaces" eth0 wlan0
```

You could use this as part of a script.

Lambros

---

