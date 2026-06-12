---
title: "Azureua  Help!!!"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by StevenP9891 on 2007-05-24
Whenever I attempt to download a torrent or just start Azureus in general it open up for a few seconds then completely closes. I dont know whats goin on. Please help me......

---

### Post by NeoLithium on 2007-05-24
If was working normally before, it could be something with a deleted torrent that is attempted to seed. I've had that happen before.  If you don't mind losing the settings that you had for it, you can delete them and it should work fine.
Open up a terminal and type (Don't forget the . before azureus):

rm -R .azureus

It will remove it and make azureus think you have a brand new installation of the program.

---

