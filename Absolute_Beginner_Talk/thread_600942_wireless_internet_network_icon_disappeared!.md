---
title: "wireless internet network icon disappeared!"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by littleasian on 2007-11-02
something weird just happened.  i just intalled a theme, but it didn't go the way i wanted it so i changed it back, but in doing so i noticed that my wireless inetwork icon has dissapered (the blue one that has 5 bars)!

im still connected, but now i can't check which connection im connected to or change my wireless setting...

how do i get it back?

---

### Post by overdrank on 2007-11-02
> **littleasian said:**
> something weird just happened.  i just intalled a theme, but it didn't go the way i wanted it so i changed it back, but in doing so i noticed that my wireless inetwork icon has dissapered (the blue one that has 5 bars)!

im still connected, but now i can't check which connection im connected to or change my wireless setting...

how do i get it back?

HI can right click on the panel select add to panel, then choose the network icon and add to panel. Hope this helps good luck! :KS

---

### Post by mdpalow on 2007-11-02
If overdrank's option doesn't work, try logging out and back in and see if it comes back.

---

### Post by RomeReactor on 2007-11-02
Hi. I think it's Network Manager that's missing. To add it back, press ALT+F2 and enter:
```
nm-applet --sm-disable
```
If it still won't show up, perhaps you're missing the Notification Area. To add it back, right-click on the top panel, select "Add to Panel..." and you can find it there.

---

### Post by xdcdx on 2007-12-17
I have the same problem. The notification area is there, but executing 'nm-applet --sm-disable' doesn't restore the icon.

I tried reinstalling nm-appleto to no avail. I experienced this problem with 7.04, and I even dist-upgraded to 7.10 to see if the problem solved, but the icon is still not there.

Any further help?

---

### Post by RomeReactor on 2007-12-17
That's odd; try executing nm-applet from the terminal, and see if it leaves any output there; if it does, please post it. Also try adding another Notification Area, just to confirm that's not the issue.

---

### Post by xdcdx on 2007-12-17
I tried adding another notification area, it didn't work

When I run nm-applet from the console it returns this:
--$  nm-applet
** (nm-applet:8740): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.39" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

Now that I see that message, I installed a local LDAP server on my machine and edited some /etc/pam.d/ files. Could that be causing it?

---

### Post by RomeReactor on 2007-12-17
That may be the problem; you can try to edit both **/etc/dbus-1/system.d/NetworkManager.conf** and **/etc/dbus-1/system.d/nm-applet.conf** and set the default policy context to "allow" instead of "deny". More information on that [here]("https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-b651559fa3b43d055bfda1c52d9b7966938a204e").

EDIT: From that same page:
> Note: if you upgraded from Breezy to Dapper and you had modified files in /etc/pam.d/ it is possible that they were not altered properly to include a reference to the pam_foreground module. /etc/pam.d/common-session should look like this:
```
session required        pam_foreground.so
session required        pam_unix.so
```

---

### Post by macogw on 2007-12-17
It's not odd.  It's being denied because network manager is still running, but the icon went *poof*.  It's a known bug.  It's just unknown as to what all the situations are that cause it to pop up seemingly at random.

---

### Post by xdcdx on 2008-01-10
macogw: you are wrong, RomeReactor's solution of editing the /etc/dbus-1/system.d/NetworkManager.conf and /etc/dbus-1/system.d/nm-applet.conf files worked fine.

It has something to do with modifying PAM files for ldap authentification, although I don't know exactly which modification caused it.

---

### Post by sheepfunk on 2008-01-12
maybe you've done this already, but I had the same problem, and my issue was I had an on/off switch on my laptop that turned wireless on and off. It was simply that being off that made the wireless icon dissapear, but it took installing windows, running a network diagnostic tool that came with my computer, and then reinstalling ubuntu to figure it out.

---

