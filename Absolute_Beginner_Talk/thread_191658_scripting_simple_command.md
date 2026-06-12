---
title: "scripting simple command"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by ColorsInMyHead on 2006-06-07
hello, this seems like something thats easy to do but i just cant figure out how to do it.

I just want an icon that i can click and it runs a shell command (so that I can put it in a menu and run it without typing it in the shell)

All I want to be able to run with the hit of a button is:
```
laptop_mode auto
```
(this requires root/sudo)

Thanks for your help, I tried playing around with making a .sh file but I couldn't figure it out.  I need this because my acpi doesnt report right to my laptop mode tools so I want to be able to hit this whenever I plug/unplug

---

### Post by fluffington on 2006-06-07
Assuming you're using GNOME:
[list=1]
[*]Right-click on the panel in the general area you want to add your button.
[*]Click "Add to Panel...".
[*]Click "Custom Applicatin Launcher" in the dialog that pops up.
[*]In the "Command" field, fill in "gksudo laptop_mode auto" (without the quotes, of course).
[*]Fill in the other boxes however you see fit (leave Type set to Application and don't mess with the Advanced tab). If you want a terminal to pop up and show you the results, check "Run in terminal".
[/list]

If you're using KDE, you'll want to use kdesudo instead of gksudo, and the rest of the process is fairly similar (though I don't have KDE installed, and so can't list off the specifics).

Edit: fixed missing parentheses

---

