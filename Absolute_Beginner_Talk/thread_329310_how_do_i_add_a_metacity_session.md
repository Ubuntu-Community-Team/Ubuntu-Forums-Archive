---
title: "how do i add a metacity session?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-01-01
i am running compiz with ati and i want to start in metacity so i can play WoW.
when i installed compiz it killed all my other session options.
how do i add a metacity session?

thanks

---

### Post by troymcdavis on 2007-01-29
You'll have to forgive me, as I'm a beryl user, not a compiz user, but I did a little research and came up found what looks like your answer at the Novell Wiki for SUSE. Here is the link:
```
[http://en.opensuse.org/Using_Xgl_on_SUSE_Linux#Enabling_and_Disabling_Xgl]("http://en.opensuse.org/Using_Xgl_on_SUSE_Linux#Enabling_and_Disabling_Xgl")
```
> If you later decide that you no longer want to use Xgl, you can come back to the Desktop Effects tool and disable it, which will reverse the process.

If you try to enable Xgl, but the login screen doesn't come back up successfully for some reason, you can use the command gnome-xgl-switch --disable-xgl as root to disable Xgl from the command line. (You will probably also need to do rcxdm restart to restart X and the login screen.) 
Just as a side note: you can also restart X by pressing Ctrl-Alt-Backspace. The latter (and probably the former) method will close most/all running applications. Let me know if that works for you!

---

