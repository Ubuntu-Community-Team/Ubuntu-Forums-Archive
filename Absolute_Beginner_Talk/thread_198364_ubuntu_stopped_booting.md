---
title: "ubuntu stopped booting"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by RORyne on 2006-06-17
At about 2:30am my power kicked off and the computer restarted. I woke up and went over to login (the login opened fine). However, once I enter username/password it goes to a blank screen (normal), but never gets to the splash screen for the different things that are loading. It just stays on a brown blank screen. I opened a terminal, started nautilus, my wallpaper showed up, but nothing else. I then tried adding a test account and rebooted, but still it freezes at the same page. Help? :(

---

### Post by x64Jimbo on 2006-06-17
Probably had very little to do with a power outage and much more to do with the update that was installed to your system between the last restart and the power outage. Many people have been reporting problems since the last round of updates. From what it sounds like, you might be looking at an xorg.conf file problem. One way to fix this would be to boot a livecd of ubuntu and then copy the livecd's autoconfig'd xorg.conf file into your hard disk's /etc/X11 directory, overwriting the recently fubar'd one. As with anything, however, make a backup of everything before you do anything.

---

### Post by RORyne on 2006-06-17
No dice. Any other suggestions?

---

