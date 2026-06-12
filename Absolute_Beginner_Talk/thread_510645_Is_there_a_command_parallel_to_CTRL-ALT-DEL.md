---
title: "Is there a command parallel to CTRL-ALT-DEL ?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-07-26
In windows we can use CAD to call up the task manager and kill any process on the system.  And I've had ubuntu freeze my system several times now and I was wondering, is there any equitable command on linux?  I now CAD restarts linux, but do we have a CAD parallel that opens a task manager of sorts on ubuntu?  

I know about the gnome system monitor, but I can't always hit the menu to go into.

---

### Post by FleetAdmiral74 on 2007-07-26
I like the little force quit button you can add to your taskbar, has served me well.

---

### Post by NT4usB on 2007-07-26
well, gnome-system-monitor = task manager and that's apples².
Alt+F2 gets you a run box you can launch it from.
If your GUI is really borked, Ctrl+Alt+F1 will switch to a terminal where you can kill whatever process (task) you want.
Lots of ways to do task manager like things in Ubuntu...

---

### Post by sonofusion82 on 2007-07-26
not sure about gnome.. for KDE, you can use Ctrl-Esc to open ksysguard

perhaps you can set a keyboard shortcut for gnome system monitor...

---

### Post by Old Pink on 2007-07-26
To kill an app that's misbehaving hold Alt, tap F2 type **xkill** in the box that pops up and click what you want to kill. ;)

---

### Post by nalmeth on 2007-07-26
>  perhaps you can set a keyboard shortcut for gnome system monitor...
sonofusion82 hit the spot

System -> Preferences -> Keyboard Shortcuts

Or the force quit button is another good option

---

### Post by Het Irv on 2007-07-26
Another Question

How about a parallel to Alt-Tab?
Its very frustrating not having it for convenience sake.

---

### Post by Depressed Man on 2007-07-26
In Compiz Fusion or Beryl with alt+tab you can get one with previous.

For the ctrl+alt=delete how do you set it to launch gnome monitor in keyboard shortcuts (I seem to only be able to modify existing ones). And thanks for the xkill command, I didn't know about that. Oh..and if you ctrl+alt+f1 into the terminal, how do you get back to the GUI?

---

### Post by paradoxchild on 2007-07-26
alt-tab is still alt-tab, and you can get a system monitor displayed with ctrl alt delete through automatix

---

### Post by sloggerkhan on 2007-07-26
ctrl-alt-f[1-7] are your terminals.Interacting with each one is like having a completely seperate terminal to the computer.  In theory you could setup a computer to run a GUI on every one of them. By default, f7 is the GUI.

So far as I can tell, alt-tab works the same way on windows and linux.....

---

### Post by Depressed Man on 2007-07-26
double post (bad ISP..bad ISP)

---

### Post by raywood on 2007-07-26
The force-quit button sounds good.  Where/how do I install it?

---

### Post by scott_g on 2007-07-26
If its really locked up, you can use Ctl-Alt-Backspace; it restarts your gui and brings you back to the login screen.

---

### Post by johnraff on 2007-07-26
> **Old Pink said:**
> To kill an app that's misbehaving hold Alt, tap F2 type **xkill** in the box that pops up and click what you want to kill. ;)
Even quicker, Ctrl + Alt + Esc gives you that killer skull right off, for me at least.

(Just tried it and killed my panel... :( I'm going to have to restart now to get it back...)

---

### Post by aysiu on 2007-07-26
Just paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete" && gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
``` After that, Control-Alt-Delete should bring up the Gnome System Monitor window

---

### Post by shen-an-doah on 2007-07-26
> **raywood said:**
> The force-quit button sounds good.  Where/how do I install it?

Right click on your panel/taskbar and select "add to panel". You can add a force quite button or a system monitor that'll display stuff like CPU usage and whatnot and if you click it, the gnome system monitor will come up.

---

### Post by raywood on 2007-07-27
The force-quit button sounds good. Where/how do I install it?

---

### Post by Mornedhel on 2007-07-27
sudo apt-get install xkill

Then move the xkill shortcut from the menu to wherever you please.

---

### Post by univremonster on 2007-08-01
> **raywood said:**
> The force-quit button sounds good. Where/how do I install it?

Raywood, right click on the toolbar at the top of the screen, select "Add to panel" and it should be one of the choices listed

---

### Post by z0mbie on 2008-03-20
> **aysiu said:**
> Just paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete" && gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
``` After that, Control-Alt-Delete should bring up the Gnome System Monitor window

& Also remove the short cut entry from **System > Preferences > Keyboard Shortcuts > Log Out**. Because they use the same short cut **<Control><Alt>Delete**, you either want to assign a different shortcut for** Log Out** or just disable it completely so there is no interference with **gnome-system-monitor** shortcut.

---

### Post by geethalakshmi on 2008-04-25
Hi,
     The link given below has the Command to kill a process in Linux.
[http://hiox.org/bypass/index.php?id=105]("http://hiox.org/bypass/index.php?id=105")

---

### Post by Lakjin on 2008-07-14
> **z0mbie said:**
> & Also remove the short cut entry from **System > Preferences > Keyboard Shortcuts > Log Out**. Because they use the same short cut **<Control><Alt>Delete**, you either want to assign a different shortcut for** Log Out** or just disable it completely so there is no interference with **gnome-system-monitor** shortcut.

its not working for me =(


EDIT: nevermind, i reloaded gui and it is working now

---

