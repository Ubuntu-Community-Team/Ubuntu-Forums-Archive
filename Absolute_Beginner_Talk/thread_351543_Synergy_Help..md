---
title: "Synergy Help."
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Avarix on 2007-02-02
I got ubuntu installed, i got my video and sound working. So i tried my luck with getting Synergy up and running. I did and it worked how you would expect... Until i made it auto start.

What i did was follow these directions from [Located here (Click)]("https://help.ubuntu.com/community/SynergyHowto#head-e0819c48796446198c68df547f83be5acbf68dff").

> System Menu->Preferences->Sessions, click the Startup Programs tab, click "Add" then just enter the Startup Command:

synergys --config synergy.conf

then click OK & close. This will start the server on a user session basis, not globally. 

I restarted to see if it worked, but now when i hit the login screen the mouse and keyboard no longer work. I'm going to assume i need to delete the session entry from recovery mode, but i have no idea how to go about doing anything in the command line unless i have "idiot" directions. 

I did boot to recovery mode and looked around the help part, but i couldn't find anything about sessions from the command line and searches here on the forums haven't turned up anything as well.

Any help would be greatly appreciated.

---

### Post by MonolithTMA on 2007-02-04
Try just this.

> System Menu->Preferences->Sessions, click the Startup Programs tab, click "Add" then just enter the Startup Command:

synergys

That will autostart it at login.

---

