---
title: "Gnome panel already running error"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by usersock on 2006-11-27
I just installed Ubuntu 6.6 and I keep getting the "I've detected a panel already running and will now quit" error. 

Someone suggested typing "killall gnome-panel" in the terminal (Ctrl-Alt-F2) to kill the panel, then using Ctrl-Alt-F9 to return to the gui. Ctrl-Alt-F9 does nothing for me, and I have no idea how to exit the terminal other than using Ctrl-Alt-Delete. Another suggestion was to select a new theme. But without a toolbar I can't figure out how to do that one either. 

I would like to try the new theme idea first, but I assume I need to do that in the terminal. How can I do this, and then exit to the gui? Any other ideas would be very welcomed!


EDIT: I figured out how to get back to the gui (Ctrl-Alt-F7). Now how do I start a new panel from the terminal?

---

### Post by faraazs on 2006-11-27
I think someone else will have a better way but press alt-f2 and type in gnome-panel and you should be good to go.

---

### Post by usersock on 2006-11-27
Alt-F2 does nothing for me. I can type Ctrl-Alt-F2 to get to the terminal tho. While in terminal, typing "run gnome-panel" gives the error "run: command not found". Typing "gnome-panel"  gives the message 

cannot open display: (null)
Run 'gnome-panel --help' to see the full list of available command line options.

EDIT: I figured out how to open the theme manager (gnome-theme-manager), but I get the error "The default theme schemas could not be found on your system. This means that you probably don't have metacity installed, or that your gconf is configured incorrectly." After reinstalling metacity ([instructions]("http://www.ubuntuforums.org/showthread.php?t=40758&highlight=default+theme+schemas")) I now have icons on my desktop, which I did not have previously. But my theme manager still gives the same error and I still get the panel errors.

---

### Post by Carlos Santiago on 2006-11-27
Ctrl-Alt-F1, F2, F3 to Ctr-Alt-F12 switch between sessions.
One of them is graphical, usually Ctrl-Alt-F9 (or Ctrl-Alt-F7).

Alt-F1 opens the application menu
Alt-F2 opens run window

You cannot run a graphical application in a terminal session. Thats why you get the error:
   cannot open display: (null)

But on terminal you can run: killall gnome-panel

---

### Post by usersock on 2006-11-27
I fixed the problem with a reinstall of 6.6. Thanks for the tips guys!

---

