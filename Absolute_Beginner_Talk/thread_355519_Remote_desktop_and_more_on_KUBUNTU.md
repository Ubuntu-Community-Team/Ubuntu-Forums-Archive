---
title: "Remote desktop and more on KUBUNTU"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by venik212 on 2007-02-07
I thought that running KDE instead of Gnome will be trivial.  I discovered that several things that worked well under gnome now need to be reset, reinitialized, or in some other way restarted.
1) Remote desktop-- I cannot find where to set the VNC server for the Remote Desktop.
I found in Internet KRDC, but this seems to be related to using kubuntu to log on a remote machine as a client, rather than it being the server.
2) ImageJ-- I ran ImageJ well from Gnome simply by clicking on the RUN script.  That no longer works, and I have not found how to get it to run other than through the terminal, which I'd rather not use.
3) Firefox had no trouble using Java in gnome, but Konqueror does. (Breaking news-- I had to tell Konqueror where the Java path was... now that part works).

I guess easy switching was just a fantasy...

---

### Post by etank on 2007-02-07
1) KRDC is a client to connect to remote machines. To make the kubuntu box available remotely you could install vncserver or check out FreeNX at [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) or on the forum at [http://www.ubuntuforums.org/showthread.php?t=1968](http://www.ubuntuforums.org/showthread.php?t=1968).
2) ImageJ-- I have no idea what that is so I'm no help there.
3) You can run Firefox from KDE if you want to instead of Konqueror.

---

### Post by venik212 on 2007-02-07
Thanks.  I had installed and used VNC server on the machine under Gnome, and naively assumed that, since I had not removed it, it is still running.  I could not find (under KDE) the menu entry that corresponds to setting up the Remote Desktop server which exitst under Gnome under SETTINGS, where I told it how to handle outside requests, etc.
ImageJ is a Java program, which I typically start from a script (a text file).  Under Gnome there was a way to tell it to run text files by clicking them, but I could not find it under KDE.

---

