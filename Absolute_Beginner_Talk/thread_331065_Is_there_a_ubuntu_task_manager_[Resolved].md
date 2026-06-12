---
title: "Is there a ubuntu task manager? [Resolved]"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by jawknee530 on 2007-01-04
I'm a windows user transferring to ubuntu and i'm wondering if there's any utilities like windows task manager for ubuntu.  i'm looking for something that will show open programs, show individual processes, allow force quits, and show cpu and memory performance/usage.  is there anything that will do this?  oddly enough not being able to hit ctrl+alt+del and having a little window pop up is starting to be my only real problem with ubuntu.  i guess ive been in windows too long.  any advice would be appreciated.

---

### Post by aysiu on 2007-01-04
Alt-F2 ```
gnome-system-monitor
``` I believe you can also assign a keyboard shortcut for this command as well:
[http://doc.gwos.org/index.php/GnomeKeyboardShortcut](http://doc.gwos.org/index.php/GnomeKeyboardShortcut)

You could even make the keyboard shortcut Control-Alt-Delete

---

### Post by Josey on 2007-01-04
yes I'm not sure how to run it from terminal but it can be added to your taskbar

right click taskbar - add to panel - system monitor

---

### Post by mcduck on 2007-01-04
Sure, there's 'System Monitor' in System/Administration/System Monitor. It does what you want.

To get Ctrl-Alt-Del-shortcut to open System Monitor do this:

1. Open Configuration Editor (hit Alt-F2 and run gconf-editor).
2. Browse to apps/metacity/keybinding_commands
3. Set the command_1 to gnome-system-monitor.
4. Browse to apps/metacity/global_keybindings
5. Set run_command_1 to <Control><Alt>Delete

That's it :)

---

### Post by 3rdalbum on 2007-01-04
Force-quits are specially easy in Ubuntu. Right-click a panel and choose "Add to panel...". Now find the "Force Quit" applet.

Now, whenever you click that panel applet, then a window, you will be asked if you want to force-quit the program that owns the window.

If you want to earn your command-line stripes, have a look at the *top* program. It lets you see at a glance what program is using up all your processor time, and you can kill it right then and there by hitting the K key.

---

### Post by Oki on 2007-01-04
Go to Applications>Terminal and then enter top will also give you an overview over witch programs that are running.

---

### Post by jawknee530 on 2007-01-04
wow, that's some of the quickest and best answers i've gotten.  thanks a lot

---

### Post by energiya on 2007-01-04
>  How to enable Ctrl+Alt+Del to open System Monitor in GNOME
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
A lot of other usefull tips can be found [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy").

---

### Post by jloehrlein on 2007-01-14
Doing this simply gives me the following error box:

"Text was empty (or contained only whitespace)"

---

### Post by jloehrlein on 2007-01-14
opps my bad I didn't captialize "control"

---

### Post by mobiu5 on 2008-05-19
I tried to set this up, and now I am getting the same error of "text was empty (or contained whitespace)" when I try to delete using the delete button.  How can I undo this so I can use my key as per normal?

Thank you,
M

---

