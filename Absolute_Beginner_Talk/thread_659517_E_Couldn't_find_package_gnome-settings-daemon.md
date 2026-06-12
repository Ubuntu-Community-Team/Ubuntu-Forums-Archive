---
title: "E: Couldn't find package gnome-settings-daemon"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by bird_gal on 2008-01-05
Hi,
I always get the message 

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

when I want to make changes to my configuration.

I tried to download the gnome settings daemon but always get this:

E: Couldn't find package gnome-settings-daemon

Don't know what to do. Can someone help please?

Nora

---

### Post by taurus on 2008-01-05
Are you running Gutsy?  Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by bird_gal on 2008-01-05
Don't know what gutsy is but here is what i get ;)

nora@linus:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-security multiverse


# wicd repository
deb [http://wicd.longren.org](http://wicd.longren.org) gutsy extras

---

### Post by Bufke on 2008-01-05
Does that message come up when you start up the computer sometimes?  Try starting it manually by typing in a terminal ```
gnome-session-daemon
```
If this is the case you can add this command to execute on startup by going to Preferences, then sessions.  Hope that helps

---

### Post by bird_gal on 2008-01-06
Bufke, I'm not sure what you mean, sorry, I'm a real beginner...
I'm basically stuck with a german laptop keyboard set to US english and I'm trying to change that back to german. All the other things just kinda pop up while I'm fiddling around with it.

Maybe have a look here, that explains the whole lot...;)
[http://ubuntuforums.org/showthread.php?t=657700](http://ubuntuforums.org/showthread.php?t=657700)

When I typed "gnome-session-daemon" in the terminal I got command not found.

Thanks

---

### Post by Bufke on 2008-01-06
Well I looked at the other post and wow there's a lot of crazy stuff going on with your computer.  Am I correct that this all started with your computer freezing?  Perhaps reinstalling from scratch might be the best way to go at this point, it should work then right?  These problems are really beyond me.  Good luck whatever you decide to do.

---

