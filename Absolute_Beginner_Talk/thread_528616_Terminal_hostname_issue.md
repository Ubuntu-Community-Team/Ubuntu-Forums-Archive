---
title: "Terminal hostname issue"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by MckayKnight on 2007-08-18
[FONT="Verdana"]Hi all seeing as I been using Ubuntu for about two to three weeks now. whenever I go in to the gnome-terminal and try changing the hostname using the command.

```
sudo hostname
```and add the rest of the arguement to change the hostname
it changes and once I close the terminal and try re-opening it it doesn't appear at all the only way to start it is by either restarting X using Ctrl-Alt-Backspace or by logging out anyway to fix this issue or is it a bug in Gnome-Terminal[/FONT]

---

### Post by nitro_n2o on 2007-08-18
Edit the file /etc/hostname

---

### Post by MckayKnight on 2007-08-18
[FONT="Verdana"]Thanks nitro_n2o that worked but is there any other way to do it through terminal without the terminal having to stop working after I used the command I also forgot to add that once I entered the command the terminal stops working, bmpx (media player) stops working, and a couple of other programs stop working I have to reboot in order to fix it[/FONT]

---

### Post by Haitao on 2008-06-20
Seems the same problem still happens in hardy with the hostname command. Editing the /etc/hostname file works though.

Fred

---

