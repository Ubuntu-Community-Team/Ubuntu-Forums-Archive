---
title: "[SOLVED] uTorrent window doesn't show"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by purdticker on 2007-07-27
I installed wine and uTorrent last night and started downloading a torrent.  It was working perfectly.

Apparently last night we had a power outage.  I started my computer and uTorrent again.

However, the uTorrent window will not show!  I see the icon in the system tray.  When I mouseover it, it says it's downloading and uploading.  If I double click on it nothing happens.  If I right click on it and choose "Hide/Show uTorrent" nothing happens.

What's the first step in troubleshooting this?

---

### Post by NESFreak on 2007-07-27
since you installed last night. If you don't care about your settings and reconfiguring wine and utorrent, just delete ~/.wine

---

### Post by purdticker on 2007-07-27
k, gunna let my downloads finish and then try that, thanks

---

### Post by Telecaster72 on 2007-07-29
Curious on how it went i had the same problems, except now i dont even get the icon in the tray, un- and reinstalled wine, downloaded a fresh utorrent.exe, but nothing happens.
I tried Deluge and Ktorrent and liked them both especially Ktorrent but i cant get them to upload so my ratio is going straight down the drain, also tried Tribler wich is just weird...
So if you got yours to work again please post how you did it!!

---

### Post by QCompson on 2007-07-30
I experience consistent problems with utorrent unless I uncheck both the minimize and close to tray options.  You won't see the tray icon anymore but I've never had any black window/disappearing window issues since then (besides, the tray icon doesn't quite fit in).  I just keep utorrent on a separate desktop.

I also had the same problem as purdticker when I exited unexpectedly once while utorrent was running.  Wiping the utorrent settings under the .wine directory fixed it for me.

---

### Post by purdticker on 2007-07-31
I'll try unchecking the close to system tray option.  My current solution is a pain.

So far, I've been deleting 4 files in:

> 
/home/purd/.wine/drive_c/windows/profiles/purd/Application Data/uTorrent
resume.dat
resume.dat.old
settings.dat
settings.dat.old


When I reopen uTorrent, I have to File -> Open the .torrent files again.  I don't lose my progress.

---

### Post by JerMe on 2007-08-02
> **purdticker said:**
> I'll try unchecking the close to system tray option.  My current solution is a pain.

So far, I've been deleting 4 files in:



When I reopen uTorrent, I have to File -> Open the .torrent files again.  I don't lose my progress.

Thanks, worked for me.

---

### Post by olavjunior on 2007-08-13
It was enough to remove settings.dat & old  for me. Had to do it a couple of times whough, but then I didn't have to reopen all my torrents.

---

### Post by purdticker on 2007-08-13
Yup same here...

---

### Post by SentientFluid on 2007-09-22
> **olavjunior said:**
> It was enough to remove settings.dat & old  for me. Had to do it a couple of times whough, but then I didn't have to reopen all my torrents.

Awesome.  Worked for me as well.  Also combined it with disabling the System Tray icon preferences and just keeping it on it's own desktop as mentioned above.  No more disappearing uTorrent. :)

---

### Post by dansued on 2007-09-24
when utorrent exits unexpectedly, settings.dat can get corrupted.

so what I did was

1. set all of your preferences and settings the way you want.
2. close utorrent completely.
3. make a backup of settings.dat

the next time it crashes, just delete your settings.dat file and rename or copy your backup over.

---

