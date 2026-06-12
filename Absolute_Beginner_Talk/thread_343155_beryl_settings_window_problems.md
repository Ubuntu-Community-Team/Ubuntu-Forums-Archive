---
title: "beryl settings window problems"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Copperteeth on 2007-01-21
I installed ubuntu edgy on my laptop and i installed beryl. For the most part i had trouble because i couldnt get the reops to download: servers must have been down. Anyway, i installed beryl and i got it running but i cant access the settings menu from the beryl tray icon, when i click it nothng happens? What should i do?

---

### Post by Shatrat on 2007-01-21
Edit the /usr/bin/beryl-settings file and change
#!/usr/bin/env python
to
#!/usr/bin/env python2.5
You have to have python2.5 installed, but then it should work like a charm.

---

### Post by Copperteeth on 2007-01-21
the begining of the file looks like this alredy:
> #!/usr/bin/env python2.5
import berylsettings
import gtk
import gtk.gdk
import gobject
gdk = gtk.gdk
and i have python 2.5 installed? doesnt # comment out stuff? should i remove that? Whats another suggestion?

---

### Post by Shatrat on 2007-01-21
Hmm, do sudo apt-get install python2.5 to install it.  After, or if it says it's already installed, you can run beryl-settings from a terminal window instead of clicking the tray icon and any errors will print in the terminal.

If you have python2.5 then I suppose you don't have the same problem I did.

the #! on the first line of a script says what binary to run the script in, often !#/bin/bash or !#/bin/sh

---

### Post by Copperteeth on 2007-01-21
ok i should have done this first but in terminal when i run beryl-settings i get this error:
> Traceback (most recent call last):
  File "/usr/local/bin/beryl-settings", line 2, in ?
    import berylsettings
ImportError: No module named berylsettings


---

### Post by Shatrat on 2007-01-21
That's the same error I was getting, but changing the first line to use python2.5 fixed mine.
I'm using beryl SVN from trevino's repository though.  Maybe you could try changing the line so that it ISNT using 2.5, just changing it to regular python.

Im not sure what else to recommend, since apparently what worked for me isnt working for your version.

---

### Post by Copperteeth on 2007-01-21
well this last line on the error message:
> ImportError: No module named berylsettings

thats an importatnt error lol
maby somethings missing? if i check the synaptics pckage manager everything needed is there?

---

