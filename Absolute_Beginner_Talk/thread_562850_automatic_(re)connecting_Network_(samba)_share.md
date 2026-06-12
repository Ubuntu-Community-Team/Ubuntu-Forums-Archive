---
title: "automatic (re)connecting Network (samba) share"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by piagent on 2007-09-29
automatic (re)connecting Network (samba) share

I'm not sure this is the right forum, I am new to ubuntu.  I have some RH exposure and enough background in hardware and software to sometimes over complicate the simple.  Also this crosses several apps: samba, mount, network, Gnome. It is possible I'm not alone on this but have seen little posted about connection sustainability.

Problem: One out of the the four computers (all running as desktops) acts as the house server, hosting several samba shares.  The other computers mount one of the shares to their users home file.  This is done with an smbmount in the session startup programs (see additional question). Don't laugh, but this file is used by screensaver (these are the pictures my wife &#8220;NEVER!&#8221; gets to see).  When the serving computer is up before the others everything works as planned.  It is when the serving computer is taken down (sorry) or comes up behind or in the middle of the the others then no pictures on one or all.  While there are other apps I could use this screensaver must have a ~/ folder or link with a fixed name.

q1)The problem to me, it seems, is that the mount is a one time action and I need the systems to actively maintain the connection.  Is there some software, script, or Gnome add-ons that can register a network     connection and monitor it for remounting?  

FYI, this was also set up as an fstab vs a session, I do like the session solution.

q2)An additional question is related to Gnome and its' sessions when saved.  Much to my surprise I did an smbmount via the terminal and then, for an unrelated reason, did a session save.  Much to my surprise, I said I was newish, I got my share mount back without doing anything.  If I smbumount-ed and saved it as expected it did not remount.  I added the smbmount in the session startup anyway, call it disbelief, but this suggested that if I needed a place to monitor what is registered it could be Gnomes session data ..... just a thought.  But how does this session feature work?

---

### Post by piagent on 2007-09-30
Can anyone suggest a better forum for this?

---

