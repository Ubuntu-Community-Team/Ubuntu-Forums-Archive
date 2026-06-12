---
title: "how do you go from cli to gui"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by OldNewb on 2008-03-10
When you hit ctrl alt and F1 - F6 it brings up a cli.  Is there a way to have that run a gui?

---

### Post by seventhc on 2008-03-10
<Alt-F7>
to get back you won't need to use <Ctrl> so just press <Alt and F7>
:)

---

### Post by seventhc on 2008-03-10
If you just want to run a terminal from within the gui go to
*Applications>Accessories>Terminal*
Then you can run your commands and stay in your desktop environment at the same time.
I wasn't exactly sure if this was what you were looking for, so decided to post it.
If you want a keyboard shortcut to open the terminal I think you have to set it up.
go to
[I]System>Preferences>Keyboard Shortcuts
[/I]There is an entry for the terminal in there already, you just have to set it up. On mine I use the *Super L* key...or you might know it as the *windows key*

---

### Post by mali2297 on 2008-03-10
If you mean that you want to run several instances of X (the GUI), then see
[http://ubuntuforums.org/showthread.php?t=185555](http://ubuntuforums.org/showthread.php?t=185555)

---

### Post by Junglizer on 2008-03-10
> **seventhc said:**
> <Alt-F7>
to get back you won't need to use <Ctrl> so just press <Alt and F7>
:)

The <CTRL> isn't necessary when you're already in init3 but its a good idea to get into the habit of using it anyways b/c some apps read <ALT> + F# as a command and most WM's use that to change desktops.

---

### Post by inksmithy on 2008-03-10
Nice alternative to having to cycle through all the menus to find a terminal is to install yakuake.

sudo apt-get install yakuake. When you hav it installed, go through the configuration to get it the way you want it and add it to your session so it starts up when you reboot.

It is similar in style to the command line in quake, dropping down from the top of the screen and presenting you with a terminal. I have mine set to appear and disappear when I hit F12, it is incredibly useful.

Alan

---

### Post by OldNewb on 2008-03-10
> **mali2297 said:**
> If you mean that you want to run several instances of X (the GUI), then see
[http://ubuntuforums.org/showthread.php?t=185555](http://ubuntuforums.org/showthread.php?t=185555)

I tried the instructions there but I get an error because I am running X in window 0 already,  this is the output:

xauth:  creating new authority file /home/me/.serverauth.8699

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

any suggestions?

---

### Post by mali2297 on 2008-03-10
> **OldNewb said:**
> I tried the instructions there but I get an error because I am running X in window 0 already,  this is the output:

xauth:  creating new authority file /home/me/.serverauth.8699

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

any suggestions?

Which command did you use?
```

startx -- :1

```

---

### Post by Dr Small on 2008-03-10
Try:
```
xinit -- :1 vt9
```

Explained:
Initiate X on Display 1 at Virtual Terminal 9.

---

