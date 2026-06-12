---
title: "Few questions (recent Ubuntu convert)"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Echow on 2006-06-20
Hey all I've just started to use Ubuntu, such a refreshing change to xp. Anyways I have a few questions:

1. Is there any way to change the 'middle mouse-click = paste' option? I tend to use this in Opera and it tends to copy text in places i dont want.

2. Everytime I try to play an audio file (oggs, mp3s, and audio from movies) there is about 1/2 a second of static before the music begins. Is there any way to remedy this? I'm using gstreamer, files were tested in amarok and totem.

3. How would I make a keyboard shortcut to get to the System moniter (eg ctrl-alt-delete just like in windows? I'm not sure if this is already set to something but it doesnt seem to have any effect atm.)

Edit:
4. This has happened only a few times, but sometimes my screen fills with garbage:
[http://img72.imageshack.us/img72/4228/screenshot22ar.png](http://img72.imageshack.us/img72/4228/screenshot22ar.png)
I think this is somehow related to updating or something, but I'm not sure.

Thanks for your help!
Edwin

---

### Post by bukwirm on 2006-06-20
Ctrl-alt-del usually reboots the computer.

You can set some keyboard shortcuts in System > Preferences > Keyboard Shortcuts

---

### Post by jimrz on 2006-06-20
[QUOTE=Echow]
3. How would I make a shortcut to get to the System moniter (eg ctrl-alt-delete just like in windows? I'm not sure if this is already set to something but it doesnt seem to have any effect atm.)
[/QUOTE]
 right click on your panel...choose "add to panel"...drag the "System Monitor" icon from the window that opens to where you would like it to appear on your panel

this will display (cpu usage is the default) in your panel and you can double click to open and access other tabs...handier than a desktop shortcut, i think

---

### Post by Echow on 2006-06-20
Hey sorry I realise i didnt make myself really clear, I meant keyboard shortcut instead of normal shortcut. I dont think ctrl-alt-delete does anything, only ctrl-alt-backspace reboots am I right?

---

### Post by aysiu on 2006-06-20
Alt-F2 ```
gconf-editor
``` Apps > Metacity

Global Keybindings > Command_1 ```
<Control><Alt>Delete
```

Keybinding Commands > Command_1 ```
gnome-system-monitor
```

---

### Post by jobezone on 2006-06-20
I don't think gnome allows to add extra actions to the ones it presents in  System->Preferences->Keyboard Shortcuts.

Just had a search and there are two packages you might want to checkout, xbindkeys and xbindkeys-config (the last one is a graphical gui to configure the previous). I haven't used this, but I assume you put xbindkeys to run automatically when you log into Gnome (System->Preferences->Session), and configure it with xbindkeys-config...

EDIT: Ah, forget my post then,  aysius's tip is simpler.

---

### Post by Echow on 2006-06-20
Thanks guys. Works like a treat.

---

### Post by rattyrat on 2006-07-11
I found these posts through Google and thought you might like to know how I got round a similar lockup on my system.

Assuming you have a second PC networked to the Linux box, install VNC, then you can log in a second time as Root and use the System Monitor to look for the locked task, and kill it.

If you cannot log in via VNC it probably indicates your system is totally locked and you need to re-boot.

Hope this helps.

RR

---

