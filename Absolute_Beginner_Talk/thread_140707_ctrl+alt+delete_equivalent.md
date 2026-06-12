---
title: "ctrl+alt+delete equivalent"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by spencewah on 2006-03-06
Hi guys,

I just switched over from windows and I'm trying to find my way around Linux (with the Kubuntu distro).  Right now I want to close the Katapult program so that it can reload and pick up some new programs I put into the K Menu. What's the best way to do this?  Does linux have a ctrl alt delete equivalent where I could find and kill Katapult?

And if I'm going about this entirely wrong, let me know that too :)

Thanks!

---

### Post by TrendyDark on 2006-03-06
Not sure how to do this by yourself, but I know there's an option in Automatix to set it up so that ctrl+alt+del is bound to the system monitor. I use it, very useful.

The link to Automatix can be found in my signature if you want to try that option.

---

### Post by aysiu on 2006-03-06
Try Control-Alt-Escape--that will change your mouse to skull and crossbones, which will kill any offending application you click on.

You can also right-click on the KMEnu and create a keyboard shortcut for ```
ksysguard
```

---

### Post by MetalMusicAddict on 2006-03-06
This is how to make CTRL+ALT+DELETE open up the gnome-system-monitor:

In a Terminal type:
**gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete**"
Then:
**gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"**

---

### Post by engla on 2006-03-06
I also think it's neat to tie a keyboard shortcut ( a hard to grab one) to xkill.

Basically, you hit the shortcut you set up, the cursor turns into a skull; you click a window and that application dies. Right clicking cancels.

---

### Post by aysiu on 2006-03-06
[QUOTE=engla]I also think it's neat to tie a keyboard shortcut ( a hard to grab one) to xkill.[/QUOTE] In KDE, the default keyboard shortcut for this is Control-Alt-Escape.

---

### Post by spencewah on 2006-03-06
oops, I just did the skull and crossbones and killed my desktop! (the wallpaper and such)

How do I bring that back?

---

### Post by engla on 2006-03-06
spencewah: I'm sorry for causing trouble like that,  It sure is a handy and effective tool! :-)
I don't know how to undo that when logged in (I don't use KDE so I don't know what takes care of the desktop, but probably the kicker or file manager does that)

[QUOTE=aysiu]In KDE, the default keyboard shortcut for this is Control-Alt-Escape.[/QUOTE]
And OSXism in KDE? Didn't think that was possible! ;-)

---

### Post by aysiu on 2006-03-06
[QUOTE=spencewah]oops, I just did the skull and crossbones and killed my desktop! (the wallpaper and such)

How do I bring that back?[/QUOTE] Try Alt-F2 and typing ```
kicker
```

---

### Post by Intell on 2006-03-06
Right now, in Kubuntu, Ctrl-Esc opens ksysguard. I didn't do any configuration.

---

### Post by Jucato on 2006-03-06
Ctrl+Esc: KSysGuard (the Ctrl+Alt+Del equivalent in KDE)
About Katapult: You don't have to close/reopen it everytime you add something to K Menu. Here's a trick: activate katapult, press Ctrl-C (configure), then just press ok. Katapult will be updated. Also, there's an option in the Katapult konfiguration to have it show in the system tray for easier access.

---

### Post by mustang on 2006-03-06
[QUOTE=MetalMusicAddict]This is how to make CTRL+ALT+DELETE open up the gnome-system-monitor:

In a Terminal type:
**gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete**"
Then:
**gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"**[/QUOTE]

Didn't work for me here (neither did the Automatix method).

Using Ubuntu 5.10 here...

---

### Post by aysiu on 2006-03-06
Then, don't type those terminal commands. You can do it graphically.

Go to Applications > System Tools > Configuration Editor
Then go to Apps > Metacity and in Global Keybindings, pick one (say, 2) and double-click on it and enter ```
<Control><Alt>Delete
``` Then go to Keybinding Commands and find the corresponding command # (2, for this example) and double-click on it and enter ```
gnome-system-monitor
```

Remember, this is assuming you're using Gnome. If you're using KDE, it's totally different!

---

### Post by MetalMusicAddict on 2006-03-06
[QUOTE=mustang]Didn't work for me here (neither did the Automatix method).

Using Ubuntu 5.10 here...[/QUOTE]
Weird. Ive used that since Warty. :-k

---

### Post by mustang on 2006-03-06
My apologies

it does indeed work I was just hitting the wrong delete (the one in the numpad)

What how can I represent the delete/period key in the numpad in the configuration editor?

---

### Post by aysiu on 2006-03-06
[QUOTE=mustang]My apologies

it does indeed work I was just hitting the wrong delete (the one in the numpad)

What how can I represent the delete/period key in the numpad in the configuration editor?[/QUOTE] Go to System > Preferences > Keyboard Shortcuts and find a command you don't use. Then set the keyboard shortcut (temporarily) to the period key on your numpad and see how it shows up. Then delete that shortcut. I think it'll be something like *KPdecimal*.

---

### Post by mustang on 2006-03-07
[QUOTE=aysiu]Go to System > Preferences > Keyboard Shortcuts and find a command you don't use. Then set the keyboard shortcut (temporarily) to the period key on your numpad and see how it shows up. Then delete that shortcut. I think it'll be something like *KPdecimal*.[/QUOTE]

Thank you asyiu for replying.

KPdecimal doesn't work. "." doesn't work and of course nothing comes up when num lock is off. 

It's a kinda trivial thing, I can probably get used to the other delete key.

---

### Post by doanotherlinux on 2007-09-22
I´ve got the same problem in Xubuntu.  How do I take care of this?

---

### Post by SpikeyMike on 2008-03-08
I am trying to configure this too, but when I go to Applications I don't see System Tools, how can I configure this?

Spikey



> **aysiu said:**
> Then, don't type those terminal commands. You can do it graphically.

Go to Applications > System Tools > Configuration Editor
Then go to Apps > Metacity and in Global Keybindings, pick one (say, 2) and double-click on it and enter ```
<Control><Alt>Delete
``` Then go to Keybinding Commands and find the corresponding command # (2, for this example) and double-click on it and enter ```
gnome-system-monitor
```

Remember, this is assuming you're using Gnome. If you're using KDE, it's totally different!

---

### Post by corney91 on 2008-03-08
> **SpikeyMike said:**
> I am trying to configure this too, but when I go to Applications I don't see System Tools, how can I configure this?

Spikey
Press Alt+F2 and enter:
```
gconf-editor
```

You can also add it to the menus if you right click and select 'edit menus'

---

### Post by SpikeyMike on 2008-03-12
Hi, thanks, I got it working :)

Spikey

> **corney91 said:**
> Press Alt+F2 and enter:
```
gconf-editor
```

You can also add it to the menus if you right click and select 'edit menus'

---

### Post by koolcracker on 2008-07-06
This just brings up the menu now to shutdown my computer, after setting ctrl alt delete to gnome-system-monitor. Why?

---

