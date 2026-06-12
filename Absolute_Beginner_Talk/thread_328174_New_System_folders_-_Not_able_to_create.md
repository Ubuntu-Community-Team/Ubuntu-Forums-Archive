---
title: "New System folders - Not able to create"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by ubdai on 2006-12-30
For some reason the new folders command under file, is not highlighted and I am unable to make a new folder to put in some codecs for mplayer.

Is this normal. Or do I need to change mu user status to get it enabled.


ubdai

---

### Post by shanepardue on 2006-12-30
"gksudo nautilus" from a terminal will open a window with root privileges. it's a security measure that you can't affect root from your username.

---

### Post by ubdai on 2006-12-30
Sorry didn't seem to work got the following

(nautilus:17399): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:17399): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

Any clues why.

ubdai

---

### Post by shanepardue on 2006-12-30
The first message is normal, but I haven't seen the second one before. The only thing I can think of is try to reboot and do it again, but I don't have much faith in that. Did it ask you for a password after you typed in that command?

---

### Post by ubdai on 2007-01-01
Did a reboot and seems to be ok.

Thanks

ubdai

---

