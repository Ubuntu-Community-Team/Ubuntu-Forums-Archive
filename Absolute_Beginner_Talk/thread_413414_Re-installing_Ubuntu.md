---
title: "Re-installing Ubuntu"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-04-19
the power has failed twice and ubuntu is corrupted, how do do an re-install

---

### Post by MrCheese on 2007-04-19
If it really is beyond salvation, you need firstly to see if you can rescue any personal data - did you create a seperate /home partition? If so, simply make sure it isn't reformatted when you reinstall, otherwise try to copy off the data to eg usb storage.

Then boot from your original install cd & proceed as before - as I said initially, if you have a seperate /home make sure it isn't included in the formatting by manually doing the partition editing rather than letting the system  just reinitialise everything. Sorry if this sounds a bit vague - it could be summed up as "install as you did the first time, but take care to save any data you need before you blow it all away".

When I set up a new system I keep a copy of my /etc/fstab so I know what partition holds which bit of the system so if I need to do a low-level rescue I at least which bit of the hard disk to look on.

---

### Post by avanrens on 2007-04-19
Thank you, only installed today so don't need to save anything.Thanks again

---

