---
title: "[SOLVED] Stupid Panel ?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by anchor1te on 2008-01-24
I seem to have lost my Network option on the panel.  The one next to Power and Sound.  Since I'm usually connected wireless, I kinda need it.  Can't find it in the options to add back.  I know it's a silly request, but I don't want to have to do a re-install.


Thanks!

---

### Post by Sidewinder1 on 2008-01-24
I'm not positive that this will work for you but it's worth a try. Right click on the Panel. Left click on 'add to panel". Look under System & Hardware and you should see "Network Monitor", left click on it, then click on "add" at the bottom of the window.
That should be it; no reinstall :-)
HTH,
Ed

---

### Post by mikewhatever on 2008-01-24
Press alt+f2 and type nm-applet. If you see the icon appear, make sure that NM works and make sure Network Manager is ticked in Systems>Preferences>Sessions. Otherwise, type nm-applet in a terminal and post the output. Pardon my ignorance, but what does it have to do with panels?

---

### Post by SunnyRabbiera on 2008-01-24
> **mikewhatever said:**
> Press alt+f2 and type nm-applet. If you see the icon appear, make sure that NM works and make sure Network Manager is ticked in Systems>Preferences>Sessions. Otherwise, type nm-applet in a terminal and post the output. Pardon my ignorance, but what does it have to do with panels?

panel applets can get the hiccups sometimes :D

---

### Post by ugm6hr on 2008-01-24
> **anchor1te said:**
> I seem to have lost my Network option on the panel

That was careless of you ;)

3 possible reasons (and solutions):

1.

First, try installing the package *network-manager-gnome* (in Synaptic)

2.

Then try this:
Alt+F2: nm-applet --sm-disable

Add the same command to your Startup Programs (System-> Preferences-> Sessions) to autostart every boot.  This runs the NM system tray monitor,

3.

Still not there?  You have probably removed the notification area on the panel:
Right-click on the panel in a blank grey area.
Add to panel
Notification Area (in Utilities)
Add

Hopefully it should be back (somewhere) now.  You can move the notification area in the panel afterwards (right-click).

---

### Post by anchor1te on 2008-01-24
Notification Area was the culprit.  Thanks for the replies everyone!!

---

### Post by ugm6hr on 2008-01-24
> **mikewhatever said:**
> Pardon my ignorance, but what does it have to do with panels?

The problem is with the Network Manager system tray applet, which is a different entity than the Network Monitor Gnome panel icon.

It *could* be a problem with the absence of a Notification Area (aka system tray) in the panel, so the applet has no place to exist.  Or, as you have stated, it could be that the applet is not running (see my previous post for the default nm-applet command).  Or, least likely, Network Manager has been uninstalled (possibly due to installation of an alternative wifi program).

I hope that clears it up.

---

