---
title: "Mouse Cursor on boot, but thats it!!"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ozmacguyver on 2007-05-26
I'm new to Ubuntu, but working at it as Windows is getting rather old. Anyway, I wasn't up to speed with root user compared to a 'general' user, so I tried to make my login name part of the root user group. After rebooting to see if it worked (manually switching via console didn't seem to work) Ubuntu doesn't work.

Basically, I get the Ubuntu Splash Screen, then it disappears, then you get the animated mouse cursor, but then that's it!! No login screen, just hangs for ever.

Does any one know is this an easy fix, or do I re-install from CD, and if I re0install, does it wipe everything, or can you fudge it like Windows and still have everything accessible, just working?


PS: I was trying to fix a synaptic error - I added the signature from WINE, which worked, but when I manually added the sudo xxxxxxxx etc..... it crashed synaptec. You cant even get into it. I was going to add me as a root user, then edit the sources.d.list to remove the incorrect entry, which is where I ended up now!!!


...........help!  I really like Linux, now that I'm hooked.

---

### Post by paddyboy on 2007-05-26
I'm no expert here, but I had similar problems to you after a dual boot failure. If you don't even get to the login screen it's something more than just passwords, etc.

I think you are at the point of a fresh install. I hope you have'nt too much to loose in the Linux side.
If you do go for a new install :
Go back over to windows and go into disk management utility.You will see the partitions you created there for Ubuntu. Right click on them and delete. Be VERY careful you don't zap the windows one(s) they will probably say something about NTFS file systems etc.
Put the CD in the drive and  install.......at the Partition options, go for the top one (guided + use freed space).
You should fill in the logon info as 'truthfully' as possible. What I mean is get the default login options etc.
Once in, go to System-Admin-Users & Groups and set up at least one other User for yourself. I added in root as well, as a failsafe. In general don't login as root unless you really know what you are doing. It's way too easy to delete stuff, etc, and there is no way of undoing it.
Hope this helps, sorry I can't give you a quick fix option.

---

### Post by ozmacguyver on 2007-05-26
Cheers.

I can boot via recovery mode, and get to the command line via the root user, so hopefully, if I can get this far, is there anyway to access user info, or the file that holds user info?......

"GDM" doesn't work for root user either..........sigh!

---

### Post by joramdam on 2007-05-26
Try unplugging every devise, and try boot...

---

