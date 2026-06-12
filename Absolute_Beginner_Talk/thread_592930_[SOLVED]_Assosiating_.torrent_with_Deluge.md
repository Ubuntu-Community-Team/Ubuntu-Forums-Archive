---
title: "[SOLVED] Assosiating .torrent with Deluge"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Vadi on 2007-10-26
Hi,

How can I assosiate .torrent files with Deluge in Firefox? I search in Preferred Applications, but there was nothing there.

Thanks!

---

### Post by Maestro23 on 2007-10-26
In FF:

Edit>>Prefs>>Content>> Manage File Types

---

### Post by CaptainInsaneO on 2007-10-26
If you associate your torrent files with Deluge in Ubuntu, it will also associate in Firefox. I've done this with Azureus because I don't like using BitTorrent.

---

### Post by Maestro23 on 2007-10-26
> **CaptainInsaneO said:**
> If you associate your torrent files with Deluge in Ubuntu, it will also associate in Firefox. I've done this with Azureus because I don't like using BitTorrent.

That way too.:)

---

### Post by Vadi on 2007-10-26
Like I said, I tried, but the "Preferred Applications" didn't have an entry for torrent.

FF preferences like those before don't have it either :(

---

### Post by Maestro23 on 2007-10-26
> **Vadi said:**
> Like I said, I tried, but the "Preferred Applications" didn't have an entry for torrent.

FF preferences like those before don't have it either :(

Can setup in File Associations as well.

Apps>> Other>> File Associations

Search for .torrent

Make Deulge the 1st app for the file type.

---

### Post by Vadi on 2007-10-26
It already first in there. But that menu looks like it's for KDE, I'm on Gnome..

---

### Post by wheredidrealitygo on 2007-10-26
Easy way to do it.

Download a .torrent, save it to disk, don't open it with anything. Right click it, go to "Open With" tab, and set it to Deluge. If Deluge isn't there already, click "add" and find deluge in your filesystem. should be in /usr/bin/deluge.

---

### Post by Inxsible on 2007-10-26
> **wheredidrealitygo said:**
> Easy way to do it.

Download a .torrent, save it to disk, don't open it with anything. Right click it, go to "Open With" tab, and set it to Deluge. If Deluge isn't there already, click "add" and find deluge in your filesystem. should be in /usr/bin/deluge.
Or when it asks you which application to use, in firefox, you can click browse and go to /usr/bin/deluge and select it.

---

### Post by Vadi on 2007-10-26
Thank you both. I should have realized the first, but the second is also very useful.

I tried finding the deluge start program, but search didn't find anything useful and I generally don't step outside of my little /home because I get lost :(.

---

### Post by Maestro23 on 2007-10-26
> **Inxsible said:**
> Or when it asks you which application to use, in firefox, you can click browse and go to /usr/bin/deluge and select it.

So many ways to to do things in Ubuntu.  I love it.:)

---

### Post by Maestro23 on 2007-10-26
> **Vadi said:**
> It already first in there. But that menu looks like it's for KDE, I'm on Gnome..

I'm in Gnome as well.

---

