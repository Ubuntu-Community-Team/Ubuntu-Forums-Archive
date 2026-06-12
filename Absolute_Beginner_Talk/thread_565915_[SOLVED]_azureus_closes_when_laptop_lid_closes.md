---
title: "[SOLVED] azureus closes when laptop lid closes"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2007-10-02
Very annoying.  I'm trying to seed but not waste laptop battery power.  Then afterwards I have to delete all of the log files to get Azureus to stop immediately closing when I open it.  Any help would be much appricated

---

### Post by e_james on 2007-10-03
I have a laptop running Windows XP and ubuntu 7.04, usually Windows. Most of the time I have Paradox for Windows (accessing network files) and Remote Desktop running. When I put the laptop into standby mode (by whatever means), the first thing it does is to shutdown the network connections. When it wakes up again the last things it does is to reconnect to the network and refresh network information. Standby therefore breaks the remote Desktop connection but this can be restarted. Paradox gets really upset and must be forcibly shut down and restarted. So before I let the PC go into standby I prefer to close Paradox and the Remote Desktop and set any file manager windows to look only at local files. It gets worse if the network changes while the PC is in standby. If I expect to take the  laptop to another location, I first have to set Paradox to see only local files and then tell Windows to disable the network connection. If Idon't follow this procedure I will end up rebooting Windows and Paradox wiil refuse to start.

I am confident that these problems could be solved by a software revision but I don't think any programmers would see the amount of work as justified.

My point is that you seem to be in a similar position. I assume Azureus is capable of handling temporary internet interruptions, so you could prepare the way by breaking your internet connection and perhaps other steps before you close the lid.

---

