---
title: "How Do I Kill Process when a Program locks"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-10
I'm a new user so please be patient. Every once and awhile, I get a program that locks up.  
This doesn't happen often but it does happen. In windows, I can control-alt-delete and
pull up either programs or process to end them if a program should lock up.

How do I do this in Ubuntu? 

Thanks  :KS

---

### Post by nest on 2007-10-10
the command is this

```
killall firefox-bin
```

if you dont know the name of the program you can do

ps -e

find the name and kill it :)

firefox-bin is an example :P

---

### Post by por100pre1 on 2007-10-10
```
pkill *program-name*
```

---

### Post by Dr Small on 2007-10-10
```
ps aux | grep *programname*
kill *pidnumber*
```

---

### Post by tgalati4 on 2007-10-10
There are several ways:

In a terminal, when firefox locks up:

>sudo killall firefox-bin

Clicking the X in the upper write corner of the offending window.  After a while, a dialog box will come up asking:  Force Quit?  Yes or No.

Run top to find the offending process:

>top  (Control C to quit)

Write down the offending process identification number, PID.  Say 666 for example.

>sudo kill 666

If that doesn't do it, escalate

>sudo kill -9 666

If the entire desktop is unresponsive--last resort:

Control-Alt-Backspace

That drops you to a console.

>startx

Will restart the graphical desktop

There are a few other ways.  Others will chime in.

---

### Post by philinux on 2007-10-10
Under System>Admin there's system monitor. Much like task manager. Easy to use too.

---

### Post by oldos2er on 2007-10-10
If you prefer a graphical way to kill processes, do this: right-click on your top panel (assuming Gnome), choose 'Add to Panel.' Choose 'Force Quit.' Now when a programs hangs, click the 'Force Quit' icon, then click somewhere in the program window.

---

### Post by Calvin349 on 2007-10-10
Just wanted to say thanks.  Reading the forums and this is EXACTLY what I needed to know.

Yeah I am very new to this myself.  Looking forward to a full convertion soon.

Thanks again,

Calvin

---

### Post by mevets on 2007-10-10
Also,
1. Alt + F2
2. Type: xkill
3. Click on the window you want to close.

---

### Post by Orbital75 on 2007-10-10
Thanks guys, Just what I needed to know...... :)

---

### Post by s.victor on 2007-10-10
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

These commands enable Ctrl+Alt+Del to open System Monitor in GNOME. You need to enter them just once. Then you can handle the same as you do in Windows.

---

