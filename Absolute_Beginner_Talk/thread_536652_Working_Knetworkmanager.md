---
title: "Working Knetworkmanager"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-08-28
I am currently hooked in through a ethernet cable, due to I click the wrong thing in the Knetworkmanager and now it is stuck in manual configuration mode and now it no longer show my wireless network card, Help please... I use this laptop for school, and I need the wireless, My friends have been no help they keep telling me to shut up and install windows, I would perfer not to I can never go back to all those blue screens :)

Any help would be great!
~J3ff

---

### Post by r4e on 2007-08-29
Hi J3ff,

Based on [this thread]("http://ubuntuforums.org/showthread.php?t=455984") , if you ever use manual configuration knetworkmanager can no longer manage wireless networks.

To fix it, the wireless configuration in /etc/network/interfaces has to be reverted back to the original settings.

I don't know the name of your wireless device, so from Konsole, could you post the output of:

sudo cat /etc/network/interfaces

---

