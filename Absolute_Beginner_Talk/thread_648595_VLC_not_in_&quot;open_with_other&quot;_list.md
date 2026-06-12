---
title: "VLC not in &quot;open with other&quot; list"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by camtheman2343 on 2007-12-23
Im a n00b to linux so yea sorry.  Im at F.F. if it matters
Well I know enough to install VLC media player using applications>add/remove programs.
So I have some mp3s and I want to be able to listen to them with VLC. I can drag and drop the files to the icon on my desktop or my top tool bar and it works fine. But if I right click and hit open with other program VLC is not on the list and I want VLC to be the default program for mp3s but I can't make it the default program if its not on the program list! any suggestions?

---

### Post by seventhc on 2007-12-23
If you want vlc to open an mp3 you can right click on an mp3 file then choose 'open with', if it's not in the list then choose 'open with other application', and if you don't see it in tha list that opens look on the bottom where you can choose 'use custom command' and type  vlc and click 'open'. To make it default once it's added you can then right click on any mp3 and choose properties then go to open with and choose vlc.
IMO there are better players for music though.
hope this helps.

---

### Post by frank002 on 2007-12-23
Right click the mp3 song and click" open with" and then" open with other application". Select " use a custom command" and hit ""browse". search for vlc in /usr/bin and double click it. You should be able to open the file with vlc.

---

### Post by drs305 on 2007-12-23
Right click on an .mp3 file. Select Open With, then Open With Other Application. Browse to your VLC app (usually in usr/bin ). After you've done that, then go back into nautilus, right click on Properties, select the Open With tab, and VLC should be displayed. If you choose that, VLC should become your default player.

If you can't find the VLC app in usr/bin you might want to reinstall it.

---

