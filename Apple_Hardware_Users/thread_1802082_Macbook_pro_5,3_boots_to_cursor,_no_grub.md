---
title: "Macbook pro 5,3 boots to cursor, no grub"
date: 2011-07-11
forum: Apple Hardware Users
---

### Post by Jalaska13 on 2011-07-11
I've just successfully installed Ubuntu 11.04 on my macbook pro, but when I boot, I just get a blinking cursor.  I've tried the following to try to fix it, with nothing working:

Press "Shift" to boot into GRUB (result: doesn't respond)
    Using liveCD, edit grub settings to allow for this (result: same as before).

Chroot using liveCD to install required video packages (result: updates work, but installing new or upgrading existing packages fails because it can't properly start jobs.  I assume this is because it wants to use resources that would exist if the system were truly booted from the HD but the resources don't exist in the LiveCD environment)

Chroot using LiveCD and try using jockey-text to install NVidia drivers as suggested on [https://help.ubuntu.com/community/MacBookPro5-3/Lucid](https://help.ubuntu.com/community/MacBookPro5-3/Lucid) by command line instead of by GUI.  Can't connect to certain sockets (the device files don't respond because they're not in the active system, I guess).

Can't think of any other solutions.  Ideas?

---

### Post by Jalaska13 on 2011-07-11
New Idea - use LiveCD's grub to boot local partition's command prompt?  Can't figure out how to get this working - shift doesn't work and hitting escape at the purple screen doesn't give me the options I need.  Maybe I'm missing something.

---

### Post by Jalaska13 on 2011-07-12
Never mind.  For some reason re-installing as an update (as if I were updating an older OS version) fixed it.  No idea why it works now or didn't before, but I'm not asking questions.

---

