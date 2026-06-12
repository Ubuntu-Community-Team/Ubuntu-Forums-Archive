---
title: "Can't copy to clipboard using NoMachine connecting to Ubuntu 10.04"
date: 2011-11-11
forum: Apple Hardware Users
---

### Post by barrys@netapp.com on 2011-11-11
Hi,
This is my setup:
MacBook Pro w/ OSX 10.7 (Lion)
Connecting to Ubuntu x86 10.04 (Lucid)
Connecting using No Machine Player Version 4.0 beta -- the only one that works with OSX 10.7
Same issue using Gnome or KDE desktop sessions.

Problem:
Cannot copy to Mac's clipboard from the NoMachine client using any flavor of copy to clipboard on the Ubuntu desktop.
Can copy to Ubuntu's clipboard and paste from that in Ubuntu in the no machine window-- just not outside of that window.
Can copy to the Mac's clipboard from a Mac program (duh!) and _can_ paste to windows in Ubuntu in the NoMachine window.  (Why would this work when copying the other way won't.  :confused:)

I updated my NoMachine client, node, and server components on the ubuntu side. 
I installed kubuntu-desktop which didn't help and f'd up the Gnome connections (my preference), so  I removed that.  Same copy paste behavior checked before and after those changes.

Sorry to blather on like I'm emailing some support person.  But, I thought more is better on providing info in case anyone has any ideas.

The settings on the nx server config (/user/NX/etc/server.cfg) are set to allow copy paste in "both" directions.  This is default.  Same behavior with or without this setting commented out.

Copy/Paste in both directions works perfectly using the NX Client v3.5 on Windows.  So, I'm sure it's this Mac NX Player 4.0 that's barfing.  Since NoMachine and Ubuntu are such good friends, I'm hoping someone on here might have some insight.

---

### Post by antonmos on 2012-02-24
I have the same problem with NX server on Centos 5.5
NoMachine is taking FOREVER to fix the bugs in NXPlayer 4.x :(

---

### Post by gordintoronto on 2012-02-24
I assume that No Machine is some kind of remote desktop? When it displays the Ubuntu screen, it's a bitmap, not text in a window. I would expect that you could copy the bitmap, perhaps into a drawing program?

---

