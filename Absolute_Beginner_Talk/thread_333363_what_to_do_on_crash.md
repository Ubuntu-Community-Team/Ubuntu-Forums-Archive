---
title: "what to do on crash"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Auria on 2007-01-07
Hi

in one day Ubuntu 6.05 froze to death 3 times... what can i do? in mac i would hit cmd-alt-esc to force quit, in windows i'd hit ctrl-alt-del to see task manager

i did some searching and found bringing a terminal with "Ctrl + Alt + F1" and then killing appropriate process - but on my computer Ctrl + Alt + F1 shows an help window!

thanks

---

### Post by nhandler on 2007-01-07
Ctrl+Alt+F1
Ctrl+Alt+F2
Ctrl+Alt+F3
Ctrl+Alt+F4
Ctrl+Alt+F5
Ctrl+Alt+F6

Those should all launch a terminal

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

The commands above will map Ctrl+Alt+Del to the system monitor.

---

### Post by Auria on 2007-01-07
Neither of Ctrl-Alt-F keys bring a terminal.

Ctrl-Alt-F1 opens an help window, Cttrl-Alt-F5 makes the desktop blink,all others do nothing

I executed the commands you gave me on a terminal, but nothing happens either when i press ctrl-alt-del

:-k

---

### Post by Auria on 2007-01-07
oh wait... does it absolutely have to be left ctrl and alt keys?
my left alt key is broken, so i use the right one

---

### Post by xpod on 2007-01-07
You could always just go to the "system monitor" via your menus and kill any dodgy processes or "ctrl-alt-backspace" is another answer to a frozen system.Other than a frozen FF i`ve never had a crash yet thankfully...
I only know the simple ways;) 

If you right click your panel and then"add to panel" theres also a "force quit" thingy in there you could stick on your panel for easy access

---

### Post by Auria on 2007-01-07
ok thanks...

but when it happened it wasn't answering to mouse clicks anymore, i could move mouse but it was completely frozen :/ oh well i guess there's nothing to do then

---

### Post by Delkster on 2007-01-07
> **Auria said:**
> but when it happened it wasn't answering to mouse clicks anymore, i could move mouse but it was completely frozen

This isn't normal. When does that happen? When running something with 3D acceleration, by any chance? What kind of video hardware do you have?

---

### Post by Patrick K on 2007-01-07
Right/left alt keys are different, at least on my system. The right alt key does nothing. The left works as expected. The keyboard isn't the problem since both work as expected in windows. I think I'll post a question on KB mapping and try to get the right alt key working like the left. Since your left key is broken, you have a bit of a problem.

---

### Post by Auria on 2007-01-07
> **Delkster said:**
> This isn't normal. When does that happen? When running something with 3D acceleration, by any chance? What kind of video hardware do you have?

It happened at least once when an app popped an error message while i was dragging files

another time was when i tried Beep Music Player (or whatever it's called... i'm in desperate need for a music player with an EQ)

(but i never even tried video hardware so can't tell - however if hardware conpatibilty continues as bad i as it has been up to now i can be assured it wont work)

Yes Patrick thanks that's what i guessed - on linux left and right alt are different :/ is there a way to change the mapping?

thanks for answering!

---

### Post by riven0 on 2007-01-07
I think if you go to Keyboard Preferences you can change the ALT key funtion.

BTW, when it freezes does CTRL + ALT + Backspace work?

---

### Post by Auria on 2007-01-07
> **riven0 said:**
> I think if you go to Keyboard Preferences you can change the ALT key funtion.

BTW, when it freezes does CTRL + ALT + Backspace work?

Well as of now it doesn't work because ALT doesn't work...

i opened the keyboardPreferences but failed to see what i should change. There's a section Alt/WinKey, but then it always talks of WinKeys and i don't see how i could use right ALT (or any other key) instead of left alt to recover from crashes.

---

### Post by riven0 on 2007-01-07
Okay, when you go to Keyboard Preferences, try choosing* Meta is mapped to the left Win-key. *Does that work?

EDIT: Then try using the Win key in place of the ALT key.

---

### Post by Auria on 2007-01-07
No =(

Still nothing happening

---

