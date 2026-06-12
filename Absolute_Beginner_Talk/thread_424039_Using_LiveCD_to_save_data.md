---
title: "Using LiveCD to save data"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by tamird on 2007-04-26
After heavy experimentation in Feisty, I managed to irreversibly screw it up. I went out to best buy and got an external hard drive, came home, plugged it in and tried to using LiveCD to get at the internal hard drive and copy files off it to the external. The system spit out that it can't copy anything, because I don't have permission to READ the file.

How do I get around this?

EDIT: some files do copy over. I think the files that refuse to copy were created by the "root" user back when I had the thing working. Can I somehow change the owner or force the LiveCD to read the files anyway?

---

### Post by tamird on 2007-04-26
bump

---

### Post by trishacupra on 2007-04-26
I'm a newbie and I managed to screw up everything TWICE yesterday and my Live CD saved the day both times.

I think I opened Nautilus using sudo to access my files. (I haven't worked out all my permissions problems myself yet.)

**gksudo nautilus**

See if that gives you the access you need. You don't even need to enter a password, since it's the Live CD.

---

