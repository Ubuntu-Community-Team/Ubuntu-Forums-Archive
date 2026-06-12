---
title: "load programs at Startup"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by ankitguptag18 on 2008-01-04
I have Ares (Torent Downloader) installed in Windows. However i m able to access it from Ubuntu  and it is downloding files in Ubuntu which i started in Windows. So i want it to Start Automatically when i start Ubuntu. I m Using Ubuntu 7.04 feisty.

---

### Post by ajmorris on 2008-01-04
hi, to do this, you must open the gnome startup options, and add a new application to startup. Then, it is as simple as putting in, the name, the command (wine <path to .exe file>) and the description. Although, if you get the app running, to continue downloading the files that you started downloading in windows, you must add the .torrent file that you were downloading from, and have the target directory to download to, the same as where windows was downloading to, then get the torrent client to scan how much is done.

---

### Post by bufsabre666 on 2008-01-04
i dont remember if ares used a extension hider like .!ut used in utorrent
but if it doesnt i say you might want to switch to a more detailed fully featured client

i suggest azureus or deluge ((or ktorrent if you want less user input))

just find the torrent files in your windows dir and set them to the download directory and it should work
i do this between utorrent in windows and azureus in linux

---

### Post by kpkeerthi on 2008-01-04
Though not related to your question... Why wine something when there good native alternatives in Linux? deluge, transmission, rtorrent, aria2. Your call.

---

### Post by ankitguptag18 on 2008-01-04
But Where do i find startup manager

---

### Post by kpkeerthi on 2008-01-04
Type **gnome-session** in a terminal.

---

### Post by kpkeerthi on 2008-01-04
System -> Preferences -> Sessions

---

