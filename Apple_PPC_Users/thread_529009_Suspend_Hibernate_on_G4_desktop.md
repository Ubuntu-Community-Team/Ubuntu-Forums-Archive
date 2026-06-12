---
title: "Suspend Hibernate on G4 desktop"
date: 2007-08-18
forum: Apple PPC Users
---

### Post by oudisos on 2007-08-18
Dear everyone,

I have Feisty running on a Apple G4 466MHz desktop with 768MB ram and ATI rage 128 AGP card. I use it as a data and print server and a place where I backup the rest of the household computers, so speed isn't really an issue.

The main problem that I am having is that it refuses to suspend/hibernate. When I had OS-X on it, it used to suspend (sleep) after 10 minutes of inactivity, and I had Wake on Lan configured on all the other computers to wake it up for printing, retrieving data or backing up..

I read that only ATI cards support sleep, which is what I have, but I couldn't get that to work. Both automatic sleep after 11 minutes of inactivity and sleep from the log off dialog lock the screen but keep the computer running.

I also couldn't find any error message under /var/messages that would tell me what the problem is.

Hibernate (suspend to disk) doesn't work either, it just locks the screen..

Any help will be extremely appreciated as I think that suspend is a major feature for both environmental and practical reasons.

Thanks,
Oudisos.

---

### Post by stmiller on 2007-08-20
Do you have the rage driver specified in your /etc/X11/xorg.conf:

Devices

Driver   "r128"

---

### Post by oudisos on 2007-08-22
> **stmiller said:**
> Do you have the rage driver specified in your /etc/X11/xorg.conf:

Devices

Driver   "r128"

Sorry I took a day to respond but I was out of town and did not have access to the desktop to check the driver.

Yes the driver is specified as r128.
Thank you for your responce,
Oudisos.

---

