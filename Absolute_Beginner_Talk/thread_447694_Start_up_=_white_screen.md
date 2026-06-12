---
title: "Start up = white screen"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-05-18
Normally after I log in, the monitor goes black for a second before loading the desktop, toolbars and all that stuff. I booted up this morning, and it goes black, and then white. Nothing happend then, and clicking/typing did nothing. I rebooted and tried again, no luck. Luckily, this account seems to work fine. What could be the problem? Is there a way to reset stuff back to defaults from this account, or do I need to boot into recovery mode?

---

### Post by FleetAdmiral74 on 2007-05-18
$ sudo bump

---

### Post by netwerx on 2007-05-18
You could try renaming or moving the ".gnome" folders in that users folder. there will be a couple.
May work, but i'm far from a expert.

---

### Post by GhostZrydA on 2007-05-18
This problem happened to me recently after i installed the "nvidia-settings" package, after rebooting i was able to login, but as soon as i went to the desktop the screen when white and i couldnt do anything.

Rebooting again didnt fix it, after a bit of research, it appeared that when i installed the "nvidia-settings" package for some reason it un-installed my nvidia driver, and since i was running the beryl manager, the system couldnt run beryl without the driver, hence the white screen.

I was able to fix it by booting to a command line and using "sudo apt-get install linux-restricted-modules nvidia-glx-new" i was able to get the computer up and running again, i wont be trying "nvidia-settings" again!

GhostZrydA

---

### Post by FleetAdmiral74 on 2007-05-20
Thanks for the help, although 

1) I have an ATI card and
2) I have not installed new stuff like Beryl :(

I tried gnome, xfice and failsafe gnome. Still no go. I did notice on failsafe gnome, I saw the toolbars appear for a second (no icons though) before it went to white screen.

and btw, I can still move my mouse and see it.

---

### Post by FleetAdmiral74 on 2007-05-20
Here is part of the log. I remember, I standby'd the comp, but when I went back in the mouse didnt work. I restarted and it worked fine, and it was after another reboot this happend. I dont know what the log means, but something about a gnome conf file might be the prob?

May 20 09:36:07 ed-desktop gconfd (root-22540): starting (version 2.18.0.1), pid 22540 user 'root'
May 20 09:36:08 ed-desktop gconfd (root-22540): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 20 09:36:08 ed-desktop gconfd (root-22540): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 20 09:36:08 ed-desktop gconfd (root-22540): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 20 09:36:08 ed-desktop gconfd (root-22540): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 20 09:36:08 ed-desktop gconfd (root-22540): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 20 09:36:38 ed-desktop gconfd (root-22540): SIGHUP received, reloading all databases
May 20 09:36:38 ed-desktop gconfd (root-22540): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 20 09:36:38 ed-desktop gconfd (root-22540): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 20 09:36:38 ed-desktop gconfd (root-22540): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 20 09:36:38 ed-desktop gconfd (root-22540): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 20 09:36:38 ed-desktop gconfd (root-22540): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 20 09:36:38 ed-desktop gconfd (root-22540): GConf server is not in use, shutting down.
May 20 09:36:38 ed-desktop gconfd (root-22540): Exiting
May 20 10:37:50 ed-desktop gnome-power-manager: (ed) Suspending computer because the suspend button has been pressed

---

### Post by FleetAdmiral74 on 2007-05-22
% sudo bump

this still really bugs me! It quit doing that, and randomly started again.

If I delete the files, it works, but only untill it randomly happens again. Then I lose me settings. Not that I change a lot, just put in some shortcuts and such...

---

### Post by gunksta on 2007-05-22
Nevermind

---

