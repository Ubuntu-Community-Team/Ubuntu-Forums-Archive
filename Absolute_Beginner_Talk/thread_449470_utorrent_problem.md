---
title: "utorrent problem"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Chemist on 2007-05-20
I run utorrent under wine but since i added a torrent for criminal minds it won't run. Below is what appears in the terminal when i run the command. Any ideas:confused:


will@will-laptop:~$ wine /home/will/utorrent.exe
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 16 lpiArray 0x33ee18
fixme:keyboard:UnregisterHotKey (0x20026,1): stub
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1

---

### Post by steve0921 on 2007-05-20
Why don't you try a native torrent client instead of utorrent in wine?
I currently use torrentflux (a web-app one that requires a LAMP setup) but have had no problems with bittornado, ktorrent, or azureus.

---

### Post by Chemist on 2007-05-20
> **steve0921 said:**
> Why don't you try a native torrent client instead of utorrent in wine?
I currently use torrentflux (a web-app one that requires a LAMP setup) but have had no problems with bittornado, ktorrent, or azureus.

i've tried using ktorrent bittornado and a few others but I've never been able to get a decent speed

---

### Post by Chemist on 2007-05-20
don't worry I've been a tool. I got it working now

---

### Post by size_XXM on 2007-05-20
Hi.
**HOW** did you get it working? I'm getting pretty much the same error when I try to instal IrfanView or Wordweb.

EDIT: are you using the ubuntu version of wine or the one from winehq.org?

---

