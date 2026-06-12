---
title: "Samba login script help"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by garradk on 2007-09-24
Hello everyone.
  Ive been banging my head on the keyboard for the last 8 hours trying to figure this out...
  I work for a school system, where we are running an ubuntu terminal server. What we are trying to do is have people out in the schools boot to network, and load the terminal session from the server while authenticating through our Active Directory on a Win2k3 server...... That all works fine,,
The problem i have has to do with finding *some* way to execute a logon script that will automatically map windows network shares on the ubuntu desktop,, much like a logon.bat would do when logging in to a regular windows client machine. The script has to have a way of discerning what group the userid belongs to in AD to map the appropriate windows shares...... (ex: T:\"userid" for a networked home drive)
 Im not sure if this makes sense to you all or not, but I figured if anyone knew how to do this, someone here would.
Many Thanks!

---

### Post by cmnorton on 2007-09-27
When you say Ubuntu terminal server, are you referring to sshd or telnetd, or some product similar to Windows Terminal Server?

As far as mapping shares, I am still a novice. From testing, as long as I can log into my Windows domain with a valid workgroup -- I know it's a domain, but the Linux login calls it workgroup -- and use something like <domain-name> and <my-name> and a password, I can map a drive. I'm not sitting at an Ubuntu system right now, so I'd have to go try this out again. I've never tried mapping from a script, but have used the "Places" applet on the desktop.

As far as figuring out who logs in and maps to what, that could be done in one of several ways: /etc/bash_profile could contain a huge case statement mapping a particular user to a mapping; you could do this individually in each user's ~/.bash_profile; or use a database.

Hopefully, someone with more experience will expand on this.

---

### Post by garradk on 2007-09-27
sorry for being so vague.. the server is edubuntu running ltsp.

---

### Post by smadon on 2008-01-30
Hello,

Any luck about your project ?

I would like to do the same thinks,

I started to do my own script to start on map the drive, but I have a problem because I need the mount command, which is only possible for sudo, and the user who connect don't have the sudo authority to mount,  
so let me know, if you resolve your problem and how you did it. :-)

Thanks
Hope to read a reply.
:guitar:

---

### Post by dcstar on 2008-01-31
> **garradk said:**
> Hello everyone.
  Ive been banging my head on the keyboard for the last 8 hours trying to figure this out...
  I work for a school system, where we are running an ubuntu terminal server. What we are trying to do is have people out in the schools boot to network, and load the terminal session from the server while authenticating through our Active Directory on a Win2k3 server...... That all works fine,,
The problem i have has to do with finding *some* way to execute a logon script that will automatically map windows network shares on the ubuntu desktop,, much like a logon.bat would do when logging in to a regular windows client machine. The script has to have a way of discerning what group the userid belongs to in AD to map the appropriate windows shares...... (ex: T:\"userid" for a networked home drive)
 Im not sure if this makes sense to you all or not, but I figured if anyone knew how to do this, someone here would.
Many Thanks!

You can create shortcuts to locations on the Gnome desktop with **smb://server/share** as the URL - I don't know how you do this in a script, though (perhaps you could create them on a system, then copy them all somewhere on your server and then copy them to the User Desktop on login??).

Otherwise you will need a simple script to mount each share separately, which should be fairly easy to do:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

