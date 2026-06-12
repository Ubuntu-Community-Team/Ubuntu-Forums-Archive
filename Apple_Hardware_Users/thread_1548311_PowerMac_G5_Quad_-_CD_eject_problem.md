---
title: "PowerMac G5 Quad - CD eject problem"
date: 2010-08-08
forum: Apple Hardware Users
---

### Post by unsound on 2010-08-08
Hi,

I'm using Ubuntu 10.04 on a PowerMac G5 Quad and I have configured it to a point where it works very well. However, one issue remains. When I eject a CD/DVD from the system (either by using the eject key on the keyboard, or the 'eject' command from the command line) the tray is ejected but then instantly pulled back in again.

This not an issue with the hardware issue as it works fine in Mac OS X 10.4/10.5. It seems that once you send an eject command to the drive in Ubuntu, another contradictory command is sent that makes it pull the tray back in.

Does anybody know what's going on?

---

### Post by linuxopjemac on 2010-08-08
known bug:
[https://bugzilla.redhat.com/show_bug.cgi?id=453095#c26](https://bugzilla.redhat.com/show_bug.cgi?id=453095#c26)

---

