---
title: "Newly Minted User."
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by TIBU0083 on 2007-06-27
Hello, 


I would just like to say, I'm hooked on Ubuntu. I have a problem with freezing. Is there a crtl-alt-del key to remove the accused app. And I have fifteen gigs on this partition of Ubuntu, but it seems like it taking up a lot of space. I haven't downloaded much. But is there anyway I could remove, or use a program to make some space. 



Thanks, 
if anyone read this. 


I'm still using ubuntu. 



Gabe. :D

---

### Post by dfreer on 2007-06-28
You can map the gnome system monitor in metacity to <Ctrl><Alt><Delete> with these two commands (this won't work in beryl, although there is way around this as well):
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

This command will clean up your local apt-get cache:
```
sudo apt-get clean
```

You can run Applications > Accessories > Disk Usage Analyzer to see what is taking up all the space.

---

### Post by starcraft.man on 2007-06-28
Ya, I wish ctrl alt del brought up the monitor by default but oh well... [here is how to key bind the monitor to ctrl alt del]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME")

Oh and Ctrl + Shift + Backspace will reset the gdm, that always works to get ya working again but it logs you out entirely and closes everything so not ideal if you only want to close one program.

That should do it, have fun :).

Edit: Rats, dreer beat me to it... by a hair.

---

### Post by dfreer on 2007-06-28
I've got ubuntuguide mapped to <Ctrl><Alt><Delete> so I can post faster <3

---

