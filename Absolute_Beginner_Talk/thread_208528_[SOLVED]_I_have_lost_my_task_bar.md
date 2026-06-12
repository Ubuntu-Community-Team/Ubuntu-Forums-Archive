---
title: "[SOLVED] I have lost my task bar"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by tbrminsanity on 2006-07-03
My computer overheated the other day and reset on me.  It went through a system scan and after it was done I didn't have a task bar anymore.  How do I get it back?  If I can't get it back how do I create a new taskbar without an existing taskbar?  Lucky for me I have a back up of my main menu and I have set the main menu to come up when I second click the desktop.  So I can still access everything in my computer.

---

### Post by aysiu on 2006-07-03
Alt-F2 and one of these commands should help: ```
xfbrowser4              xfce-mcs-manager        xfs_check
xfburn                  xfce-setting-show       xfs_copy
xfce4-about             xfd                     xfs_db
xfce4-appfinder         xfdesktop               xfs_freeze
xfce4-autostart-editor  xfhelp4                 xfs_growfs
xfce4-kiosk-query       xflock4                 xfs_info
xfce4-menueditor        xfmedia                 xfs_io
xfce4-mixer             xfmedia-remote          xfs_logprint
xfce4-panel             xfmountdev4             xfs_mkfile
xfce4-session           xfontsel                xfs_ncheck
xfce4-session-logout    xfprint4                xfs_quota
**xfce4-taskmanager**       xfprint4-manager        xfs_repair
xfce4-terminal          xfrun4                  xfs_rtcp
xfce4-terminal.wrapper  xfs_admin               xfterm4
xfce4-tips              xfs_bmap                xfwm4
``` I'm betting on the one in bold.

---

### Post by tbrminsanity on 2006-07-04
The system has deteriated even more.  I am forced to re-install.  Lucky for me I have a backup of my files before I lost everything.

---

### Post by jis on 2006-09-07
It is xfce4-panel you should have run.

---

### Post by jis on 2006-09-07
I removed the task bars for testing purposes by "killall xfce4-panel". I am not sure, if this is wise thing to do since I just noticed that I can not quit Xubuntu. Applications -> Quit gives the following dialog:

"Unable to quit session.

Quitting the session requires that Xfce's session manager (xfce4-session) is running, but it was not detected.  Please quit Xfce via another means."

I am not sure, if this is due to killing and restarting xfce4-panel. How should I quit then?

---

### Post by jis on 2006-09-07
Well, I can quit - restart by giving "sudo shutdown -r now" at terminal. I also found out that the dialog mentioned in the previous post happens if you have restarted xfce4-panel by giving command "xfce4-panel" in the Run Program dialog, not if you have restarted it in terminal. Strange indeed. Can anybody explain why it matters how you restart the panel?

---

### Post by Billi on 2007-07-09
If you can open the menu on the screen, then go to **Setting/Autostarted Applications**, (right under the Settings Manager on mine). Click Add, in the Command box put   **/usr/X11R6/bin/xfce4-panel**    and I just put xfce4-panel in the name box, I didn't bother with a description. Log out and then restart, you should have a panel now. I'm sure this isn't the correct way to do this, but I'm not very smart, so I have to do things the easy way. Hope this works for you.

Billi

---

### Post by jis on 2007-07-10
In Xubuntu applications on panel and the panel itself  are launched automatically normally, in my experience. That is, if you have not quited them explicitely. I have only Print queue applet and Restricted Drivers Manager in the Autostarted Applications dialog, yet I get panels and many applications and panel items launched automatically, when I log in. Could it matter, if you check "Save session for future logins" when you log out?

---

