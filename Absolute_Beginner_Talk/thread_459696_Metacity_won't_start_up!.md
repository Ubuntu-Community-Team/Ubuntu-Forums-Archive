---
title: "Metacity won't start up!"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by King_Critter on 2007-05-30
Or at least, I asume it's a problem with metacity...

I just installed the metacity-themes package. When I went to the themes manager and selected one (I can't remember which) my screen blinked and the top/bottom bar (or docks, or menubar, or whatever you want to call them) disapered. So I hit Ctrl-Alt-Backspace, logged back in, the splash screen popped up and it froze. I restarted, and the same thing happened. I tried restarting in recovery mode, with the same result. I removed the metacity-themes package from the command line, but that didn't help any... So I need help. Badly. 

Oh, and in case anyone is wondering I'm posting this from Lynx.

---

### Post by sawjew on 2007-05-30
I have had a similar problem before and it was due to an incomplete or corrupted theme.  The problem is that now your system is trying to load that theme at start up and encountering the same error.

first try deleting your ~/.gtkrc2.0 file and restarting gnome

if that doesn't work try using the method in post #9 here [http://ubuntuforums.org/showthread.php?t=346496&highlight=restore+default+desktop]("http://ubuntuforums.org/showthread.php?t=346496&highlight=restore+default+desktop")

If you can only boot into the failsafe terminal you should be able to start nautilus from the terminal using the command```
nautilus
```

or you can remove them from the command line using```
rm -rf ~/.gnome
```
 etc. for each of those directories.

This will restore you to a default Ubuntu installation after a gnome restart but will unfortunately delete all your gnome settings so that you will need to reset everything.

If you can start nautilus you may want to browse through the ~/.gnome2 directory and see if you can find any theme related files and delete them individually.

Unfotunately I am at work using Windows now so I can't check up which directories to delete.  I hope this helps.

---

