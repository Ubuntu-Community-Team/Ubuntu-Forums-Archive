---
title: "Crashing Amarok"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by LitusMayol on 2007-08-16
Hi. 
I'm having a problem with my dear Amarok. It crashes like a Windows program. I mean, I start it, and since that it crashes. Everything's slowly,change a song may pass a year, and searching a song in my collection is eternal! ... 

That's what the Console says:

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
qstring_to_xtp result code -2
qstring_to_xtp result code -2
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8098008 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8098008 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Qt: Locales not supported on X server
QInputContext: no input method context available
QInputContext: no input method context available
qstring_to_xtp result code -2
QPainter::begin: Cannot paint null pixmap
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?


thanks.

---

### Post by Happy_Man on 2007-08-16
Ah yes.... the eternal "KDE WENT OFF ON VACATION AND I DON'T KNOW WHAT TO DOOOOOOO" question. Don't worry. Nobody knows why or how KDE does this. Just log out and log back in. It should be fine.

---

### Post by eyemou on 2007-08-16
Weird - I think this is what is happening to me...

[http://ubuntuforums.org/showthread.php?t=527094](http://ubuntuforums.org/showthread.php?t=527094)

Anyhow, after "opening" Amarok (watching it try to load, and then not open on the desktop), do amarok and amarokapp appear as running processes? Is adept_manager working for you? And lastly, does running amarok from the command line, but with sudo, work for you?

If the answer is yes, then I am in the same boat... :(

---

### Post by LitusMayol on 2007-08-16
Eyemou! You have just descrived the other problems i have had this days. But Adept has started to work again after a week, it get normally by itself. So... I don't know... I restarted the computer twice, and then Adept was workin

I still having the problems related with Amarok: watching it try to load, and then not open on the desktop, crashing when is time to start another song,... 

Yes we're in the same boat.



Happy_Man! How do I log out? I didn't understand what you meant. 

Thanks anyway!

---

### Post by eyemou on 2007-08-16
By "log out", just click on the KDE menu, and there should be an option near the bottom to "log out". A window will pop up with some options ("shutdown", "restart", "logout" and something else...). Either click "logout", to return to the login/splash screen, or "restart" to completely restart the system.

---

### Post by LitusMayol on 2007-08-17
It doesn't works... I prove it, but it still "crashing"

---

### Post by LitusMayol on 2007-08-21
I've solvede it.

I ereased all the configurations in my user, and i have started again.

---

### Post by Happy_Man on 2007-08-21
> **eyemou said:**
> Weird - I think this is what is happening to me...

[http://ubuntuforums.org/showthread.php?t=527094](http://ubuntuforums.org/showthread.php?t=527094)

Anyhow, after "opening" Amarok (watching it try to load, and then not open on the desktop), do amarok and amarokapp appear as running processes? Is adept_manager working for you? And lastly, does running amarok from the command line, but with sudo, work for you?

If the answer is yes, then I am in the same boat... :(
@eyemou:

You do know amarok is set to not show itself on the desktop, but will instead show up as an icon down in the tray right?

---

### Post by LitusMayol on 2007-09-02
Anybody can help me? please!

---

