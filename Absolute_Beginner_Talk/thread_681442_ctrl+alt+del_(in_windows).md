---
title: "ctrl+alt+del (in windows)"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-29
Hello!
By pressing ctrl+alt+del you can see the running process and cpu and ram and network stat. Is there something like that in linux? 
Thanks.

---

### Post by aysiu on 2008-01-29
> **Hoom@n said:**
> Hello!
By pressing ctrl+alt+del you can see the running process and cpu and ram and network stat. Is there something like that in linux? 
Thanks.
Yes. It's called *gnome-system-monitor*, and you can bind it to Control-Alt-Delete if you want by pasting these two commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

```

---

### Post by ctswhole on 2008-01-29
Yes, you can use the system monitor to gain the information you would get in Windows using ctrl+alt+del.  Go under System --> Administration --> System Monitor.  Or as an alternative, right click the top menu bar and select "Add to Panel", add the System Monitor.  Whenever you click on the system monitor icon, it brings up a window with the information you're looking for.

---

### Post by Amstell on 2008-01-29
> **ctswhole said:**
> Yes, you can use the system monitor to gain the information you would get in Windows using ctrl+alt+del.  Go under System --> Administration --> System Monitor.  Or as an alternative, right click the top menu bar and select "Add to Panel", add the System Monitor.  Whenever you click on the system monitor icon, it brings up a window with the information you're looking for.

thanks...i couldn't get the one above to work but what you have will work perfect. 

cheers

---

### Post by NullHead on 2008-01-29
> **aysiu said:**
> Yes. It's called *gnome-system-monitor*, and you can bind it to Control-Alt-Delete if you want by pasting these two commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

```

> **Amstell said:**
> thanks...i couldn't get the one above to work but what you have will work perfect. 

cheers

You need to past those commands one line at a time to have the effect you want.

---

### Post by Amstell on 2008-01-29
> **NullHead said:**
> You need to past those commands one line at a time to have the effect you want.

i did do one at a time and all i get is the logout menu

---

### Post by Hoom@n on 2008-01-29
Thank you.

---

### Post by sparticis on 2008-01-29
> **Amstell said:**
> i did do one at a time and all i get is the logout menu

as do i

---

### Post by apostate on 2008-01-29
Seems like maybe something in Ubuntu has already bound to that....some kind of hack to make it act like a Windows NT workstation.  Try binding to CRTL+ALT+Home or something, and it works.

---

### Post by Hoom@n on 2008-01-29
I tryed ctrl+alt+home. It's nothing. But thank you for your help. Now I know what to do.

---

### Post by apostate on 2008-01-29
Right, so enter:

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>End"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

And now Crtl+Alt+End ( End seemed intuitive!) should give you the Task Manager thing (gnome-system-monitor)

Works here.

---

### Post by Hoom@n on 2008-01-30
Thank you.

---

### Post by mleffler on 2008-03-01
Me, I'm stubborn.  I found that using the commands below worked.
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```
What I did first though was to route the current keyboard shortcut to ctrl-alt-end.
I did this by going to System/Preferences/Keyboard Shortcuts then under Desktop changing Log out.
So, for those like me I hope this helps sort it out some.

---

### Post by Rolcol on 2008-03-01
Technically ctrl + alt + delete would bring up many different options.  ctrl + shift + escape is specific for the task manager without having to go through that menu.

---

### Post by mason215 on 2008-03-01
> **apostate said:**
> Right, so enter:

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>End"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

And now Crtl+Alt+End ( End seemed intuitive!) should give you the Task Manager thing (gnome-system-monitor)

Works here.

thanks, that worked

---

### Post by FuzzyUnicorn on 2008-03-03
> **Rolcol said:**
> Technically ctrl + alt + delete would bring up many different options.  ctrl + shift + escape is specific for the task manager without having to go through that menu.

That's only on XP Professional. On windows 9x and XP Home, ctrl+alt+del brings up the task manager. Not sure what happens on all the different versions of Vista.

---

