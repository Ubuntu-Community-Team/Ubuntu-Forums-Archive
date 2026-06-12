---
title: "Command works in one launcher but not another"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Ambidextrous on 2007-07-03
I just installed a Win32 game under Wine.  After a bit of tinkering with the sound driver, it works flawlessly.  The installation put a launcher on my desktop.  Since I'd rather have it in my Application/Games menu, I copied and pasted the  command  into a launcher on the menu.  Why it won't work from the menu when it works perfectly from the desktop or a panel?

The command is
```
env WINEPREFIX="/home/terry/.wine" wine "C:\PROG~FBU\RETU~AKG\wolfSP.exe"
```Learning Linux reminds me of one of my old BBS taglines:  "The documentation only makes sense after you know how to use the software."

Terry

---

### Post by jfinkels on 2007-07-03
> **Ambidextrous said:**
> I just installed a Win32 game under Wine.  After a bit of tinkering with the sound driver, it works flawlessly.  The installation put a launcher on my desktop.  Since I'd rather have it in my Application/Games menu, I copied and pasted the  command  into a launcher on the menu.  Why it won't work from the menu when it works perfectly from the desktop or a panel?

The command is
```
env WINEPREFIX="/home/terry/.wine" wine "C:\PROG~FBU\RETU~AKG\wolfSP.exe"
```Learning Linux reminds me of one of my old BBS taglines:  "The documentation only makes sense after you know how to use the software."

Terry

try doing this:```
env WINEPREFIX="/home/terry/.wine" && wine "C:\PROG~FBU\RETU~AKG\wolfSP.exe"
```does that work?

If not, run the command in a terminal ('Applications > Accessories > Terminal') and tell us the output.

---

### Post by Ambidextrous on 2007-07-04
No better than the original.  Both start the game's loader, but the loader can't load and start the game.  It quits with: 

"Wolf 1.0.0 win-x86 Nov 13 2001
----- FS_Startup -----
Current search path:
H:\/main

----------------------
0 files in pk3 files
----- CL_Shutdown -----
-----------------------
Couldn't load default.cfg"

I now realize that the command does, in fact, "work".  It starts the loader for the game, which is all it's supposed to do.  Wine and the game itself should take over from there.  It puzzles me that exactly the same command, when issued from a launcher created by Wine and the game during installation, works - meaning the loader actually loads the game and it's possible to play it - but when the same command is issued from a gnome launcher I created,  the game loader can't find a configuration file and quits.  FWIW, Nautilus can't find a file named "default.cfg" either.  And the only files in the package with .cfg extensions are in the same directory as the executable called by the command.

I'm sure there's a logical explanation, but for the time being I'm going to fall back on Clark's Law.  (Any technology, sufficiently advanced, is indistinguishable from magic.)

To add annoyance to confusion, the desktop launcher created during installation disappeared overnight.  When I started the pc when I came home from work it was nowhere to be found.

I can still play the game:

```
cd "/home/terry/.wine/drive_c/Program Files/Return to Castle Wolfenstein"
wine WolfSP.exe
```in the gnome terminal will work, but in terms of user-friendliness, it's a bit under-whelming.  I even tried to launch it from a shell script.  From within the terminal it works, so it saves me a bit of typing, but apparently scripts don't work in launchers.

Thanks for the suggestion.  I'm just a bit frustrated right now.

---

