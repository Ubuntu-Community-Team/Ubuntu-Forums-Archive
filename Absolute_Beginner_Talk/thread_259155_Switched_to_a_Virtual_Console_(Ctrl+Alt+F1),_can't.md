---
title: "Switched to a Virtual Console (Ctrl+Alt+F1), can't get back to X (Gnome)"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Zyzzyx on 2006-09-17
OK, so I thought I'd try swapping to a virtual console, had seen it mentioned a few times. Pressed Ctrl+Alt+F1 and Blammo---  text login entry. That's cool, logged in, did some stuff, logged out. But now I want back to Gnome and my good GUI-ness. (posting this from a separate system, hooray for KVMs)

I've tried Ctrl+Alt+F2 thru F12, nothing. I can tell that Gnome is still running somewhere, I've still got tunes running.

Help?!

---

### Post by rccharles on 2006-09-17
> **Zyzzyx said:**
> OK, so I thought I'd try swapping to a virtual console, had seen it mentioned a few times. Pressed Ctrl+Alt+F1 and Blammo---  text login entry. That's cool, logged in, did some stuff, logged out. But now I want back to Gnome and my good GUI-ness. (posting this from a separate system, hooray for KVMs)

I've tried Ctrl+Alt+F2 thru F12, nothing. I can tell that Gnome is still running somewhere, I've still got tunes running.

Help?!
It may take a moment to switch.  Should be ctrl+alt+f7.  You can press on ctrl+alt+f7 several times.

You can restart the gui by doing from you console session (ctrl+alt+f1):
 
sudo bash
init 1
init 2
exit

Please note you will loose everything in you gui session when you do the init 1

Also, ctrl+alt+f2 through ctrl+alt+f6 should bring you into additional console sessions.

Robert

---

### Post by Zyzzyx on 2006-09-17
Ah, thanks for the info on F7.

Got a slightly interesting result. Went for Ctrl+Alt+F7, waited awhile, went for it many more times, waited, nothing. By chance I did it again, but differently. ;)  I had been using my right-side Ctrl and Alt keys, but using the left-side pair and the F-keys got me right back into the GUI. Seems that the right-side pair is only recognized while in X, not while at the Console.

Anyway, all better now. Thanks.

---

### Post by rccharles on 2006-09-18
> **Zyzzyx said:**
>  using the left-side pair and the F-keys got me right back into the GUI. 

Good to know.  I use the left side keys ... by accident ... and didn't know they were required.

Robert

---

### Post by Anduu on 2006-09-18
FYI a simple ALT-F7 works...no ctrl

---

### Post by kraymore on 2007-08-30
when i switch to console i am unable to ALT-F7 back into Gnome.  when going to ALT-F7 i only get an hourglass mouse pointer but no redraw of the xserver screen.  there are some tasks i wished i could do from console and not have to rely on terminal windows.  i'd love to get some troubleshooting feedback on this.  wouldn't know how to fix it.

---

