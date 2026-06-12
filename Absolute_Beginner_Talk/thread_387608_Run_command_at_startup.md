---
title: "Run command at startup"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by MR Bacardi on 2007-03-18
I need Ubuntu to run a command at startup, as the current user.
More specificly I need it to run:
irexec --daemon
I have tried putting it into System => Settings => Sessions => (The tab to start programs)
However, eventhoug this do run the command at startup, it sometimes make my mouse freeze.

Should I put the command somewhere else, or can I fix the mouse freezing problem?

---

### Post by Obor on 2007-03-18
make a file called lets say .irexec in your home
```
gedit ~/.irexec
```

and paste
```
#!/bin/bash
irexec --daemon
```

into it, save it, make it executable and add ~/.irexec into your startup sessions
That should do it, i think

Edit: To make it executable
```
cd ~/
chmod +x .irexec
```

---

### Post by MR Bacardi on 2007-03-18
Thx, seems to be working :)

---

### Post by arron on 2007-03-18
If you have a few scripts, place it into your ~/bin folder, whih is added to your path.  If you use a gnome terminal, you will need to move

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi


from ~/.bash_profile to ~/.bashrc, gnome terminal doesent parse .bash_profile for some reason.

---

### Post by garrison on 2007-08-21
You'll want to ensure that only one copy of irexec is running, e.g. I have:
```
#!/bin/bash
killall irexec
killall irxevent
irexec -d
irxevent -d
```

---

