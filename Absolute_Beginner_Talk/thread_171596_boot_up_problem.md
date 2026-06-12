---
title: "boot up problem"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Ryanology on 2006-05-07
When I start up my computer it automatically opens  two personal folders and starts running two programs  ( open office and eye of the Gnome ) even after I close them out and then restart the computer they come back in the same order , the two personals on desktop one, the programs on desktop three. This isn't a huge problem since I can just close them out everytime but would rather not. Any help would be appreciated. Thanks.

---

### Post by elamericano on 2006-05-07
Are these programs in System->Preferences->Sessions->Startup Programs tab?

Actually, I'd like to know how you manage to open something on a separate desktop. It would be great to open system logging on a desktop I don't use.

---

### Post by Ryanology on 2006-05-07
No they are not there, I have in startup programs : update notifier , Gnome power manager, and Gnome volume manager.

---

### Post by JLu on 2006-05-07
Try this, Ryanology:

1.  Close all windows and get your session looking just the way you want it to look when you log in.
2. Use Alt-F2 to bring up the "Run Application" window.
3. Type 

gnome-session-save

in the Run Application window and click the "Run" button.

4.  Your session setup should now be saved!  Log out and log back in to try it.

---

### Post by JLu on 2006-05-07
[QUOTE=elamericano]
Actually, I'd like to know how you manage to open something on a separate desktop. It would be great to open system logging on a desktop I don't use.[/QUOTE]

If you're running the default Gnome setup, you can use the workspace switcher (bottom right corner of your desktop) to switch to a different desktop with a click of the mouse, then you can open new windows there, return your previous desktop, etc.  You can also move existing windows from one workspace to another by 

1. dragging their little icons around in the workspace switcher,  or

2. using the "move to workspace..." menu item in the window's "window menu" (accessed via a left-click on the icon at the left end of the window's title bar, or right-click on the window's button in the bottom panel of your desktop).

Quick keyboard shortcuts to switch workspaces: Alt-Ctrl-RightArrow, Alt-Ctrl-LeftArrow, 

Have fun!

---

### Post by Ryanology on 2006-05-07
That corrected the problem. Thanks a lot JLu. Im really digging Ubuntu , help like this makes it easy to like.

---

### Post by elamericano on 2006-05-07
JLu, thanks for that. I didn't know #1. I'd seen #2, but I normally do #3) switch to the alternated desktop and launch it from there.

What I actually wanted to do was add: tail -f /var/log/syslog
to my startup programs, but tell it to open on desktop 2.

Maybe I can use gnome-session-save to achieve this result.

---

### Post by Mustard on 2006-05-07
Wow.  I didn't know you could drag the icons on the workspace windows. :)

---

### Post by JLu on 2006-05-07
[QUOTE=elamericano]
What I actually wanted to do was add: tail -f /var/log/syslog
to my startup programs, but tell it to open on desktop 2.

Maybe I can use gnome-session-save to achieve this result.[/QUOTE]

Ah, I see.  Any luck yet?  Here's one way that works for me: use
```
gnome-terminal --command="tail -f /var/log/syslog"
```
to open a new terminal with the desired command running in it, 
move the new terminal to desktop 2, then do gnome-session-save.
I'd love to hear a more elegant solution, though!

---

### Post by elamericano on 2006-05-09
This is better:

gnome-terminal --command="tail -f /var/log/syslog" && wmctrl -t 1 -r :ACTIVE:

wmctrl was suggested to me another forum, and it's half of what I am looking for. The ability to identify the window you want to act on is somewhat limited, but it's a great tool for automation nonetheless.

Hopefully I will be able to write my own custom launcher that can tell an apps to open where I tell them too, but for now, at least I can open them in the active desktop and move them where I want.

---

