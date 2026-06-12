---
title: "Configuring fluxbox..."
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-04-22
Can anyone give me some information on how to configure fluxbox.  I've been able to change the themes in the .fluxbox/init file but how do I add programs to the right click menu.  I've tried adding paths to programs in the .fluxbox/menu file but it didn't work.  Right now when I open the right click menu all I see is xterm, restart, and exit.  Thanks for the help; I couldn't find anything through searching the forums that specifically addressed my problem.  I can launch anything I want with xterm, but I would really like to trick out fluxbox like the pictures I have seen searching through google.

---

### Post by IYY on 2006-04-22
Are you using the correct syntax:

[exec] (ApplicationName) {/path/to/program}

---

### Post by mcmillan on 2006-04-22
There's good instructions on the fluxbox [website]("http://www.fluxbox.org/docbook.php"). That's probably the best place to start for figuring out how to configure fluxbox

---

### Post by echo $USER on 2006-04-22
[QUOTE=IYY]Are you using the correct syntax:

[exec] (ApplicationName) {/path/to/program}[/QUOTE]

No, I was just using /path/to/program.  I used the syntax you specified, but that did not do the trick.  Here are my init, apps, and menu files if someone wants to take a look, maybe the problem lies in there.  

I'll check out the site mcmillian suggested in the meantime.

Thanks.

---

### Post by Gustav on 2006-04-22
Your menu file should begin with:
```
[begin] (Fluxbox)
```
and end with:
```
[end]
```
look at this for an example of a working file:
```
[begin] (Fluxbox)
  [submenu] (X-terminaler) {}
    [exec] (Gnome Terminal) {/usr/bin/gnome-terminal} </usr/share/pixmaps/gnome-terminal.xpm>
    [exec] (xterm) {/usr/bin/xterm} </usr/share/pixmaps/gnome-terminal.xpm>
  [end]

  [config] (Configuration)
  [submenu] (Configuration2) {}
    [exec] (Keyboard shortcuts) {/usr/bin/fluxkeys}
    [exec] (Config tool) {/usr/bin/fluxconf}
  [end]
  [submenu] (Styles) {}
    [stylesdir] (/usr/share/fluxbox/styles)
    [stylesdir] (~/.fluxbox/styles)
  [end]
  [workspaces] (Workspaces)
  [reconfig] (Reconfigure)
  [exec] (Run program) {/usr/bin/fbrun}
  [restart] (Restart)
  [exit] (Exit)
[end]
```

---

### Post by mcmillan on 2006-04-22
I'm not sure what you want to do with the apps file, but I don't think it will do anything as it is right now. It can be used to start programs when fluxbox starts and also stores settings about the placement of windows. For autostarting the syntax is [startup] {command}

---

### Post by echo $USER on 2006-04-22
Thanks for the help you all.  I obviously had an old version.  I removed the version I installed through the package manager and rm -rf ~/.fluxbox/*, and installed the latest version on fluxbox's wesite.  The newer version is working a lot better than the older one.   Thanks again.

---

### Post by echo $USER on 2006-04-22
Thanks again for all the help.  But I have one more question:  Lets say I want to start nautilus minimized.  Like if I have [startup]{/usr/bin/nautilus}, what do I need to do to have it minimized automatically once it loads?  Thanks.

---

### Post by mcmillan on 2006-04-22
I'm not sure if there's something built into fluxbox for that but I don't think so. I do know that if you get a program called devil's pie it can do that, plus a lot more (set which desktop to open it, set positions, not show them in the taskbar). It's a pretty handy little program, there's some instructions with how to use it somewhere on this forum.

---

