---
title: "Nautilus problem?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mathnerd314 on 2008-01-03
Hello,

On a few occasions, all the icons on my desktop spontaneously disappear. Furthermore, I am unable to access my Home folder or anything else on the filesystem from the "Places" menu. The only solution seems to be rebooting.

I can still access everything through the terminal, so I'm guessing it's a problem with Nautilus. Does anyone know how to fix it?

I'm on a fairly ordinary Gutsy installation with Gnome, and I haven't done anything too terribly weird.

Thanks.

---

### Post by aktiwers on 2008-01-03
Sounds like Nautilus is crashing..  have you tried to reinstall or run nautilus from terminal after the crash and see what errors it gets next time it crashes?

---

### Post by mathnerd314 on 2008-01-03
Last night I typed "nautilus" into the terminal and nothing happened for about five minutes; it didn't even display any error messages. (This morning it seems to be working fine, after a reboot.)

---

### Post by Don_Shifty on 2008-02-16
hello
i have the same problem and i tried the following in the terminal:
nautilus --browser
nautilus
nautilus --geometry=GEOMETRY
nautilus -q
nothing helped! 
it crashed while copying a file from an external hd.
what could help? installing a new file browser? reinstalling nautilus?
thanks for your help!

---

### Post by crf on 2008-02-16
I had nautilus crash all the time and I guess it was due to something wrong with either the .gconf or .gconfd files in the home directory.

You may also try backing up, by renaming, the .gconf and .gconfd files in your home directory, and logging out and back in. Your desktop specializations will be undone, but you can test whether it prevents nautilus from crashing. Afterwards, if it doesn't help, you can revert the the .gconf and .gconfd files and get your desktop back. If that does help, you can revert the .gconf files and try editing them to try to discover what is wrong, or just recreate your personalised desktop.

---

