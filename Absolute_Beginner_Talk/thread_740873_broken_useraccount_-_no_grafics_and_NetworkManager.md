---
title: "broken useraccount - no grafics and NetworkManager"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Jense on 2008-03-31
Hi,
My main UserAccount is broken. Ignoring the settings in xorg.conf the screen is on a 640X480 resolution. Also so networkmanager is screwed. The symbol keeps flickering on and of and the system logs indicate that linux is constantly restarting eht0. 
Now killing the KnetworkManager and manually discovering a DHCP will give me a working connection. Also, when I go down to console and login as root, restart the xserver, everything works just fine. 
So the account is somehow broken, but not totally. I would like to recover that, but have no idea what the problem might be.
Last steps:
Yesterday I installed FireFox 3 beta and created a bunch of symlinks to have my plugins working.
Last Shutdown before the problem appeared was not clean. The system hung on "system will now halt" where I had to shut down hard. I already tried fsck.ext3 on unmounted filesystem, but no errors where reported.

Hope you can help.
THX

---

### Post by Jense on 2008-03-31
Please - somebody

---

### Post by Jense on 2008-03-31
ok some more information maby somebody can help me with that...
so, I figured out that this service dhcdbd was not working with the knetworkmanager. Restarting this service will reenable my network. But it is a workaround not a solution. 
My graphics are back to normal after a dpkg-reconfigure...
I wrote
```
 /etc/init.d/dhcdbd restart
``` into rc local, but this had only the result, that I have to restart the dbus service as well. 
Any ideas?

---

