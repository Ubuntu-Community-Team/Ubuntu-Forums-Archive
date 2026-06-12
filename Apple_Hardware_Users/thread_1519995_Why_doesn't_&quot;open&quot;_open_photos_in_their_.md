---
title: "Why doesn't &quot;open&quot; open photos in their default app?"
date: 2010-06-29
forum: Apple Hardware Users
---

### Post by DarkestRitual on 2010-06-29
I might have to tweak a setting or something else I didn't know about, but as of right now my Ubuntu 10.04 AMD64 bit VM running in now Oracle *shudder* VirtualBox. I don't suspect it has anything to do with my VM set up, I'm thinking more I have to probably set a default image application probably?

Thanks in advance,
Jason

---

### Post by sgosnell on 2010-06-29
Open does open files with their default app, if there is one.  In Nautilus, you can Edit/Preferences/Media to change the default app.

---

### Post by DarkestRitual on 2010-06-29
I should have been a bit more clear. I'm talking in the command line. I changed the settings with Nautilus prefs, and nothing happened when I tried ```
open ./1.jpeg
``` at the command line.

---

### Post by sgosnell on 2010-06-29
Open is not a valid command in any shell I've used.

---

### Post by DarkestRitual on 2010-06-29
[http://ss64.com/bash/open.html](http://ss64.com/bash/open.html)

The default shell in ubuntu is bash, yes?

Also it works just fine in OS X.

---

### Post by lykwydchykyn on 2010-06-29
You want
```

xdg-open file.whatever

```

That will use the desktop file associations set in GNOME, KDE, whatever.

"open" is a shell command for opening a program in a new VT.

---

### Post by sgosnell on 2010-06-29
Ubuntu isn't OS X.  That link is simply wrong, at least for that command.  xdg-open, as posted by lykwydchykyn, does work.  I've never used that, but there are lots of shell commands I don't normally use.  There are just too many for me to memorize.

---

### Post by DarkestRitual on 2010-06-29
Thank you. I obviously know that OS X is a modified BSD based OS and has some custom preferences for the terminal, however I figured that site would be right since it has a different page dedicated to the OS X terminal. Either way, thanks for the xfg-open command, that is what I was looking for, I think. I'll have to try it out later on tonight.

---

### Post by sgosnell on 2010-06-30
Xdg-open isn't actually an internal bash command, it's an external executable, located in usr/bin.  Open is an executable located in /bin, but it doesn't actually work in Ubuntu.  The man page for open shows openvt, not open, and that's for use in a virtual terminal.  I'm not sure of other distros, I've never had occasion to try it.  It makes no difference whether you use bash or another shell, both are external executables, not internal shell commands.

---

### Post by DarkestRitual on 2010-06-30
Good to know!

---

