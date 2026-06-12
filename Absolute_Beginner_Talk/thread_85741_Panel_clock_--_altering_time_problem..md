---
title: "Panel clock -- altering time problem."
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by elder68 on 2005-11-03
Presently I am using Kubuntu 5.04, and to change the date and the time,I have never been able to do it from the panel. A reader on this list suggested the following:

-$ sudo /usr/bin/kcmshell kde-clock.desktop

This brought up the required utility and I was able to make changes to the date and time. The other day when we changed back to ordinary time, I noticed that the panel clock had changed. The time was in error and instead of showing the date it was showing "Los Angeles". This pariticular timing of this error may simply have been coincidence.

So I resorted to the above to make the changes, but nothing changed on the Panel. The utility is showing the right date and time but the panel is still showing Los Angeles and the wrong time and give out the following error:

Error: "/var/tmp/kdecache-william" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
/usr/sbin/ntpdate

Any help with this would be appreciated.

Thank you,

---

### Post by Kapre on 2005-11-03
[QUOTE=elder68]Presently I am using Kubuntu 5.04, and to change the date and the time,I have never been able to do it from the panel. A reader on this list suggested the following:

-$ sudo /usr/bin/kcmshell kde-clock.desktop

This brought up the required utility and I was able to make changes to the date and time. The other day when we changed back to ordinary time, I noticed that the panel clock had changed. The time was in error and instead of showing the date it was showing "Los Angeles". This pariticular timing of this error may simply have been coincidence.

So I resorted to the above to make the changes, but nothing changed on the Panel. The utility is showing the right date and time but the panel is still showing Los Angeles and the wrong time and give out the following error:

Error: "/var/tmp/kdecache-william" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
/usr/sbin/ntpdate

Any help with this would be appreciated.

Thank you,[/QUOTE]

Bill - Are you using NTP to synch your clock? If you do, can you remove it (search in the forum for "NTP" - sorry I'm in the office and have limited time) because I think  its the one that's messing your system clock.

K

---

### Post by elder68 on 2005-11-03
[QUOTE=Kapre]Bill - Are you using NTP to synch your clock? If you do, can you remove it (search in the forum for "NTP" - sorry I'm in the office and have limited time) because I think  its the one that's messing your system clock.

K[/QUOTE]

I'm not too sure. I did a "locate" and came up with a whole list of stuff that seems to "NTP" If this is the problem, how do I remove it?

Thanks for your suggestion,

Bill.

---

