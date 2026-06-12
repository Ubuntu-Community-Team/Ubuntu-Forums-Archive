---
title: "Ctrl-Alt-Del Alternative?"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by ymmotrojam on 2005-10-27
I know I can go into System Monitor and manage running processes, but is there a keyboard shortcut for that?

---

### Post by Mustard on 2005-10-27
Is this what you are looking for?

[Custom Keyboard Shortcuts]("http://www.ubuntuforums.org/showthread.php?t=79560&highlight=keyboard+shortcut")

Personally, I have the system monitor 2.12.1 applet running on my top bar and when I click on it, it opens system monitor.  This is achieved by right clicking on your top bar and choosing 'add to panel', then going down the list of applets and choosing system monitor.

Another obscure feature I found with Ubuntu is that if you click multiple times on the 'close window' widget on applications that have frozen it will bring up a dialog to shut down the misbehaving application.

---

### Post by Qrk on 2005-10-27
ctrl alt del opens up the system monitor in breezy. Thats basically what it does in windows. If you want to restart x, use ctrl alt backspace. 

Also you can use ctrl tab to reach a new window if your mouse isn't working in one.

---

### Post by kakashi on 2005-10-27
if you want to kill a process from system monitor then place a force quit button on 
you menu bar.

---

### Post by ymmotrojam on 2005-10-27
Hmm... ctrl-alt-del does nothing for me.

---

### Post by ashrack on 2005-12-15
[QUOTE=ymmotrojam]Hmm... ctrl-alt-del does nothing for me.[/QUOTE]
likewise
Wil try the keyboard shortcuts guide

---

### Post by MetalMusicAddict on 2005-12-15
Heres how to set Control-Alt-Del to the system monitor using Gnome.

In a terminal type or copy/paste:
**gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"**
Then:
**gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"**

This should set you strait.

Also search the fourms a little more. I have posted this about 4 other times. :)

---

### Post by bfonseca on 2006-01-17
Hi, 
Don't know if you have figured it out yet...So I have a different solution to figuring out how to find out all active processes. In a terminal type:

$ ps -ef | less      (you can do it w/o the | less)

and to kill the process:

$ kill -9 <PID>

the PID stands for process ID (well at least I think it does)

well anyway I hope this is what you were looking for.

Brian

---

### Post by hen3rz on 2006-01-17
> Heres how to set Control-Alt-Del to the system monitor using Gnome.

In a terminal type or copy/paste:
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
Then:
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

This should set you strait.

Also search the fourms a little more. I have posted this about 4 other times. 
Sweeet works perfectly.

---

### Post by dolny on 2006-03-20
How to do the same under Kubuntu? I mean system monitor on Ctrl Alt Del?

---

### Post by mlind on 2006-03-20
[QUOTE=MetalMusicAddict]Heres how to set Control-Alt-Del to the system monitor using Gnome.

In a terminal type or copy/paste:
**gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"**
Then:
**gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"**/QUOTE]
[/quote]

Great tip, thanks!

I had totally forgot how to do that.

---

### Post by MetalMusicAddict on 2006-03-20
Weird thing is I cant get it to work In Dapper. A look at gconfig shows it all there but it doesnt work. :-k

---

### Post by mlind on 2006-03-20
[QUOTE=MetalMusicAddict]Weird thing is I cant get it to work In Dapper. A look at gconfig shows it all there but it doesnt work. :-k[/QUOTE]

I'm using Dapper and shortcut works ok.
I actually used gconf-editor, but followed the paths in your example.

---

### Post by RS3York on 2006-03-20
[QUOTE=dolny]How to do the same under Kubuntu? I mean system monitor on Ctrl Alt Del?[/QUOTE]


Ctrl-Esc should bring up the system monitor for you in Kubuntu.

---

### Post by Lakjin on 2008-07-14
> **MetalMusicAddict said:**
> Heres how to set Control-Alt-Del to the system monitor using Gnome.

In a terminal type or copy/paste:
**gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"**
Then:
**gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"**

This should set you strait.

Also search the fourms a little more. I have posted this about 4 other times. :)

its not working for me using 8.04 =(

EDIT: nevermind, i reloaded gui and it is working now

---

