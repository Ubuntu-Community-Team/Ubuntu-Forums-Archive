---
title: "Lost my Panel Manager"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by RRK on 2007-12-12
I signed in today and my Panel Manager no longer works. I right-click on the desktop then click Settings,then Click Panel Manager and nothing happens.  I have no system tray nor any other panels that use to have.  I am running either Fawn or Gibbon -- :confused:can't remember updating to Gibbon but I think I did.  
I am running XUBUNTU so this must be the xfce-panel manager?

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by RRK on 2007-12-12
I am farther along but still stuck.  If I execute 'xfce4-panel' in a terminal then everything comes back but it won't stay when I logout.  It seems that somewhere the command 'xfce4-panel' was removed from a script.  The question is: what script??

---

### Post by sourcemorph on 2007-12-13
well a temporary work around for your prob will be to add a manual entry in the System/Preferences/Sessions thing for xfce4-panel.. this will add the panel to the startup list..

---

### Post by RRK on 2007-12-13
It's working again.  I know what actions I took but I don't understand.
1. I executed 'xfce4-panel' from a terminal.
2. I right clicked the desktop, selected Settings, then Panel Manager.
3. I made a minor change to one of the panel definitions in an effort to cause an update to occur.
4. I logged out and logged back in and the Panel Manager was running again. - woohoo!
5. I shutdown, it neveer completely shutdown so I hit the power button in the morning (8 hours later) to power it off then powered it on again.
6. Logged on and the Panel Manager is still working - woohoo again!.

Apparently making my little change caused some xfce code to run that reestablished the execution of the panel manger startup command in the right startup script.

---

