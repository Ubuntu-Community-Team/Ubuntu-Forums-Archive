---
title: "Question about command line ability in Nautilus..."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by dpzektor on 2007-05-23
I am running a few emulators in Ubuntu. Some are command line based, and I am currently trying to get these functional with a simple double click in Nautilus. Some of the emulators however want their options after the filename. For example:

Dega uses it's options in a great way for Nautilus. I can associate a file with the command line emulator, as well as add a "-fs" command so that the program will execute the given rom when double clicked, at full screen. In other words, in the "Use a custom command" entry, I can simply put "dega -fs" on the properties of the romfile.

But, there is another emulator (Osmose) that I would like to run this way, with a few options added such as -fs and -joy, BUT, the emulator wants the options AFTER the filename like so (at a command prompt):

osmose gamename.sms -fs -joy

HOW can I get this to happen from within Nautilus using the custom command? If I add:

osmose -fs -joy

Well, it obviously will not load because as far as the program is concerned, "-fs" is the gamename which does not exist. 

It's a long shot, and I am not expecting there is a way to do it, but I figured I'd ask. I hope I am at least making sense to somebody, as I am finding this kind of difficult to explain.

---

### Post by chamberlain2006 on 2007-05-23
Maybe make a script so that there will be an option to load with a specific program in the right click menu.  I can show you how if you want to do that.

---

### Post by benanzo on 2007-05-23
You can just put the command in a script and set the custom command to execute that.

Make a file called osmose_gamename.sh (or whatever you want)
with these contents:
```

#!/bin/bash
osmose gamename.sms -fs -joy

```

then right click the file and select Properties -> Permissions  and check the box that says **Allow executing file as program**

---

### Post by chamberlain2006 on 2007-05-23
Make a file called "Open with Osmose" in the directory /home/username/.gnome2/nautilus-scripts and place 
```

#!/bin/sh
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
        osmose $uri -fs -joy
done


```
inside.  Then, in terminal, do
```
cd ~/.gnome2/nautilus-scripts
sudo chmod +x Open With Osmose
```
Then, run "killall nautilus" in terminal.  There should now be an option in the right click menu to "Open with Osmose".

---

### Post by dpzektor on 2007-05-23
Nice one! Thanks for the fix. I'll have to study more on scripts...seems you can automate almost anything if you know what you are doing. Myself, still getting there :)

---

