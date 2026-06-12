---
title: "control-alt-esc"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by gjtoth on 2006-11-25
I've tried a search but to no avail. 

Under my old distro (KDE), if an app froze up I could hit ctl-alt-esc and it would bring up a skull & crossbones that I could click on the app with and that would kill it.  Is there something like that in Ubuntu (Gnome)?

---

### Post by junglepeanut on 2006-11-25
I normally use the terminal, try reading 

man kill
and
man pkill

you could probaly also set a hot key to bring up something like a task manger then choose to kill it from that.

---

### Post by Delkster on 2006-11-25
I don't know if there's a key combination (or whether you can configure one), but you could try adding the "force quit" applet to a panel. You can add applets to a panel by right-clicking on empty space in the panel and selecting "add to panel". Look for a "force quit" applet or something like that and drag it to the panel.

Note: These instructions are rough. I currently have my desktop set to a non-English language and I'm not sure about the exact names in English.


Edit: Another possibility is to use Alt+F2 to bring up the "Run Command" dialog and then entering the command "xkill".

---

### Post by rfruth on 2006-11-25
I have and the force quit applet on my Gnome Panel and its great !

---

### Post by AndyCooll on 2006-11-25
The simple answer is no.

You can create a command using the Configuration Editor. Apps-->Metacity
Then edit global_keybindings and keybinding_commands to create your own. I now use Ctrl+z for this purpose for IIRC Ctrl+Alt+Esc is by default used for something else entirely.

:cool:

---

### Post by Izkata on 2006-11-26
> **Delkster said:**
> I don't know if there's a key combination (or whether you can configure one), but you could try adding the "force quit" applet to a panel. You can add applets to a panel by right-clicking on empty space in the panel and selecting "add to panel". Look for a "force quit" applet or something like that and drag it to the panel.

Note: These instructions are rough. I currently have my desktop set to a non-English language and I'm not sure about the exact names in English.

Yes, it is called "Force Quit" in English, and I have it on a panel as well.  The instructions are exactly correct - the icon looks like a window being ripped in two.

---

### Post by nickburns on 2006-11-26
ps -ef

then

kill -9 'thread number' 

this will kill the application

---

### Post by argie on 2006-11-26
> **nickburns said:**
> ps -ef

then

kill -9 'thread number' 

this will kill the application

Or:

killall <applicationname>

---

