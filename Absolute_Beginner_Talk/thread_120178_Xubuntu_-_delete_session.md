---
title: "Xubuntu - delete session?"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by johnraff on 2006-01-21
I've got two sessions available when I log in to xfce right now: "default" and "new".
However I broke something in "default" and the taskbar doesn't work, and windows dont have the close/minimize/restore buttons, they obscure the panel etc...

Anyway, "new" is fine and I'd just like to remove the "default" session, and use "new" as the new system default.
Can I do that? I've searched around all the settings to no avail.
Thanks,
John

---

### Post by aysiu on 2006-01-21
Have you tried just having XFCE save the session at each logout (see screenshot)? Alternatively, you can try ```
sudo cp ~/.config/xfce4-session/xfce4-session.rc ~/.config/xfce4-session/xfce4-session_backup.rc
sudo nano ~/.config/xfce4-session/xfce4-session.rc
``` and replacing it with ```
[General]
SessionName=Default
SaveOnExit=true
AutoSave=true
PromptOnLogout=true
DisableTcp=true
``` with ```
[General]
**SessionName=new**
SaveOnExit=true
AutoSave=true
PromptOnLogout=true
DisableTcp=true
```

---

### Post by johnraff on 2006-01-23
Thanks a lot aysiu :)
Just unchecking the box for "display chooser on login" has got it.
I don't really need to select different sessions I think.
(not really sure what sessions are for to be honest...)

---

### Post by aysiu on 2006-01-24
[QUOTE=johnraff]
(not really sure what sessions are for to be honest...)[/QUOTE] A session is basically what's going on... if I save my session with a Nautilus window open and Rhythmbox up, I'll return to a session with a Nautilus window open and  Rhythmbox up.

If I don't save my session, I'll start up, and nothing will be there.

---

### Post by johnraff on 2006-01-24
Oh OK.
Up to now (on Win98 ) I've always closed everything before shutting down, just to keep things simple.

---

