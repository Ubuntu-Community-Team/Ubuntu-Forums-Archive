---
title: "White screen after 8.04 update"
date: 2009-01-23
forum: Apple Hardware Users
---

### Post by TODDMAN on 2009-01-23
I did the 200+ update using update manager, but during the upgrade I had a power failure at my house. Now when I boot into 8.04 it shows the login screen & once I'm login all I get is a white desktop. The mouse still moves, but can't see anything.

---

### Post by cyberdork33 on 2009-01-23
I am pretty sure it is a graphics driver / compiz problem. Because your update died it is probably a good idea to reinstall with the latest CD. You can boot from the LiveCD and backup files on your current install.

---

### Post by TODDMAN on 2009-01-23
> **cyberdork33 said:**
> I am pretty sure it is a graphics driver / compiz problem. Because your update died it is probably a good idea to reinstall with the latest CD. You can boot from the LiveCD and backup files on your current install.

Isn't there a way to get into terminal & fix this, without re-installing?

Thanks,

---

### Post by cyberdork33 on 2009-01-23
> **TODDMAN said:**
> Isn't there a way to get into terminal & fix this, without re-installing?

Thanks,
you could probably fix the screen, but there is no telling what state your system's files are in if you were in the middle of an update. upgrades, even when successful, are often iffy anyway.

You can boot in safe mode, or if it works, can switch to a terminal (ctrl+alt+f1) to get to a commandline. When I have had the white screen, I would login (sometimes blindly), then when the desktop was sure to be up, hit alt+f2 to open the run window and execute 'metacity --replace' then you should be able to see the desktop.

---

### Post by TODDMAN on 2009-01-24
> **cyberdork33 said:**
> you could probably fix the screen, but there is no telling what state your system's files are in if you were in the middle of an update. upgrades, even when successful, are often iffy anyway.

You can boot in safe mode, or if it works, can switch to a terminal (ctrl+alt+f1) to get to a commandline. When I have had the white screen, I would login (sometimes blindly), then when the desktop was sure to be up, hit alt+f2 to open the run window and execute 'metacity --replace' then you should be able to see the desktop.

I did the run window (metacity --replace), then ran Synaptic to finish installing updates, so far everything seems to be back to normal.

Thanks,

---

### Post by mkvnmtr on 2009-01-25
I have had the internet connection fail in the middle of downloading updates and when it reconnected it seemed to just pick up where it left off. I think it might be a bigger problem if it was in the middle of installing the cached files.

---

