---
title: "Internet Connect"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by carrajung on 2007-01-11
I have just installed Ubuntu 6.10 and can't see how to connect to the internet using my dialup modem.  I have gone to 'Network' under admin as per Ubuntu 6.06 but it doesnt have an activate button.  Im sure that this is due to my stupidity but please help,  this is driving me nuts.

---

### Post by ieee488 on 2007-01-11
I've found that easiest way to do what you want to do is to open up a Terminal windows.
Then type **sudo wvdialconf**. Ubuntu will go and look for modems.
Note what it finds.
Then install gnome-ppp and use the /dev/ttyS#  that was found for your modem.

---

### Post by carrajung on 2007-01-11
Thanks for the info. But this still doesnt get me connected.  Any other ideas?  Idont think Ubuntu should be this complicated for such a simple task!

---

### Post by nonpareilpearl on 2007-01-11
For some reason in order to connect to the internet I need to enter 'sudo dhclient' between boots. Maybe that will help?

---

### Post by ieee488 on 2007-01-12
> **carrajung said:**
> Thanks for the info. But this still doesnt get me connected.  Any other ideas?  Idont think Ubuntu should be this complicated for such a simple task!

What exactly is the problem?

Still doesn't get you connected how? You don't hear the modem dialing? Your ISP is dropping your call? What exactly?????

I have used the same procedure with OpenSUSE 10.1, Ubuntu 5.10, and Ubuntu 6.06 to dial into my ISP.

---

