---
title: "How to find Command to run applications"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-04-22
How do you find what the command is to run any application?  More specifically right now I want to find the commands for GNotify to make it run on startup and for Rhythmbox because gtkpod needs a media player specified to play music files and I don't have it's default player (which runs with the command xmms)

Thanks

---

### Post by SOULRiDER on 2007-04-22
The command is usually the anme of the application in lowecase letters. You can also make use of Tab completion, just type the first few letters and press tab twice, it will show all the opctions.

---

### Post by zhinker on 2007-04-22
Thanks, that did it for now, but do you know if there's a place where I can get the name if your way doesn't work?

---

### Post by click4851 on 2007-04-22
This has always been a bit of a challenge for me as well, and one I think many people that are not intimate with the CLI run into.

---

### Post by bapoumba on 2007-04-22
> **zhinker said:**
> How do you find what the command is to run any application?  More specifically right now I want to find the commands for GNotify to make it run on startup and for Rhythmbox because gtkpod needs a media player specified to play music files and I don't have it's default player (which runs with the command xmms)

Thanks

```
~$ which rhythmbox
/usr/bin/rhythmbox
~$ whatis rhythmbox
rhythmbox (1)        - music player and library for tagged files using GStreamer

```

Are you sure about gnotify ?
```
 ~$ which gnotify
~$ whatis gnotify
gnotify: nothing appropriate.
```

---

### Post by zhinker on 2007-04-22
Sorry, it's actually called Gmail Notify

---

### Post by Rinzwind on 2007-04-22
After installing with synaptic look at 
properties
installed files.
(only works for installed software)

After that it's just common sense.
Example:

/.
/usr
/usr/bin
**/usr/bin/beryl-manager**
/usr/share
/usr/share/doc
/usr/share/doc/beryl-manager
<..>
/usr/share/pixmaps
/usr/share/pixmaps/wm-select.png
<..>
/usr/share/icons/hicolor/22x22/apps/beryl-manager.png

Inside /usr/bin it's more than likely to be an executable (there are more places tho ;) )

---

### Post by bapoumba on 2007-04-22
> **zhinker said:**
> Sorry, it's actually called Gmail Notify
Then run the which command with gmail-notify, it should tell you the pathnames of the files which should be executed.

---

### Post by zhinker on 2007-04-22
thanks, but that method seems to just give you the file path of the program you're using.  What I would like to know is a method to find the command name for the program itself, like figuring out that gmail notify's command path is gmail-notify and not something else; I want to know if there's a way to find that besides simple (educated) guess and check

---

