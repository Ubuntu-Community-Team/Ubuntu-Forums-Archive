---
title: "Updates are Automatic?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by rgd55 on 2007-04-24
Since installing 7.04 I noticed that the hard drive will periodically start spinning just after logging into
Ubuntu.I was able to find by typing "top",that the update manager was running.Can this process be
placed into manual so that I can choose weather to accept the updates?

---

### Post by eentonig on 2007-04-24
Updates are still requiring me to approve them. So I doubt if that's the issue.

---

### Post by freebird54 on 2007-04-24
It certainly should be giving you a choice of modes.  (auto, auto dload only, manual only - and 4 classes of things to update).  Not sure how to catch it when you have it auto already though!  Anything through System->Administration->Update Manager available as settings?  (on wrong version right now to check)

---

### Post by Spr0k3t on 2007-04-24
Go to settings/preferences/sessions and check the list there.  You should see there is a background task for handling system updates.  By default the update manager requires approval prior to installing any updates.  You can disable the automatic updates completely in the session manager, but it's not recommended FWIW.

---

### Post by rgd55 on 2007-04-24
I have Update Manager,but no option to place it in manual.

---

### Post by rgd55 on 2007-04-24
You can disable the automatic updates completely in the session manager, but it's not recommended FWIW.

Ok,my Sessions,Update Notifier is still checked.I heven't been notified of any updates since installing
7.04.Have there been any so far?

---

### Post by freebird54 on 2007-04-24
You might get a time zone tracker update - I got it last night.  Normally an icon shows up on your top panel to tell you about it.  (also usually a big yellow balloon so you don't miss it!)

---

### Post by darrenm on 2007-04-24
There haven't been any updates since Feisty was released.

---

### Post by C-A on 2007-04-24
I have not been notified of any updates. However, I ran the update manager manually and there was an update for automatix. Is the update manager only notifying of updates in the regular repo's?

---

### Post by ddg41 on 2007-04-24
I am trying to upgrade my 6.06 to 6.10 but update manager says I am upto date and does not give me the option to update the version. I tried running this line in terminal but nothing different happened. gksu “update-manager -c -d”
So any advice for a definate newbie who is trying to convert after 12 years of windows would be appreciated.

---

### Post by darrenm on 2007-04-24
edit the file /etc/apt/sources.list and change any instances of dapper to edgy. then run ```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

