---
title: "VMWare server install trouble on 6.10"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by pbwuk on 2006-10-29
Hey, complete noob here. Trying to get VMWare server running on 6.10. It seems to install fine up until this point:

> In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
/usr/share/applications/vmware-console-uri-handler.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
Trying to find a suitable vmmon module for your running kernel.

After that it continues without a problem. When I try to click VMWare server in the Applications/System Tools menu, it thinks about it but does nothing. I then tried "vmware" in terminal and got this:

> vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


So I ran the command it says to run and it runs fine up until the /usr/share/pixmaps] point and does the same as during the installation (above). I also tried as I saw on another thread with: "LD_PRELOAD=/usr/lib/libdbus-1.so.3 vmware", but the same thing occurs. Any ideas what I need to do to get it running? ](*,) 

Thanks in advance.

---

### Post by pbwuk on 2006-10-29
sorry I forgot to say it's Ubuntu Edgy Eft 6.10 if that's important

---

### Post by RyanTMulligan on 2006-11-13
I confirm having the same problem.

---

### Post by Bachstelze on 2006-11-13
Hmm, funny, I had that too during the install but VMWare still works like a charm. Are you pretty sure you don't get anything else ?

---

### Post by g7kse on 2006-11-15
Me too...ran the script and told me that everything else had been unistalled but the install script still refused to do it's business.

Should I look elsewhere to uninstall stuff?

---

### Post by Nico-D on 2006-11-20
Hi all,

I had exactly the same problem as pbwuk and I solved it by dowloading the latest VMware-workstation (5.5.3) built on 11/16/2006.
I did not notice any problem with this version. :-D 

[http://www.vmware.com/download/ws/](http://www.vmware.com/download/ws/)

Hope this helps,
-- Nico-D

---

