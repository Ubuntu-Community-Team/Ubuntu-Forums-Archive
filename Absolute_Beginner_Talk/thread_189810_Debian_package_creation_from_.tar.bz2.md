---
title: "Debian package creation from *.tar.bz2"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by rjcube on 2006-06-05
Can a Debian package be created from a *.tar.bz2 file? I know it can be done with *.rpm but is it possible with *.tar.bz2?

But in more specifics, I want to install Last.fm Player by doing more then just having it wherever I unpacked it, I want it on the applications list.

---

### Post by vidak on 2006-06-05
Isn't this software avaiable in any repositories? Have you added universe/multiverse repositories in your list (/etc/apt/sources.list) too?

If the package is still not avaiable, you should unpack the tarball somewhere (do you have to compile this stuff?), compile it using 
./configure 
and
make
then instead of entering 
sudo make install
use 
sudo checkinstall
(you should have the checkinstall utility installed)
You can read about checkinstall here:
[https://wiki.ubuntu.com/CheckInstall](https://wiki.ubuntu.com/CheckInstall)

Did I answer your question?

---

### Post by bruenig on 2006-06-05
from what I understand the last.fm player was formerly called audioscrobbler or still is and last.fm is just the url of the website. Either way doesn't matter. If you want audioscrobbler for the purpose of sharing the music you listen to and all that such to last.fm and your profile, you can install the audioscrobbler plugin to a different media player and then just use that media player.

For instance, xmms has an audioscrobbler plugin.
```
sudo apt-get install xmms
sudo apt-get install xmms-scrobbler
```

That should serve the purpose if you don't mind using a different media player to achieve the same result.

---

### Post by Donshyoku on 2006-06-05
[QUOTE=bruenig]from what I understand the last.fm player was formerly called audioscrobbler or still is and last.fm is just the url of the website. Either way doesn't matter. If you want audioscrobbler for the purpose of sharing the music you listen to and all that such to last.fm and your profile, you can install the audioscrobbler plugin to a different media player and then just use that media player.

For instance, xmms has an audioscrobbler plugin.
```
sudo apt-get install xmms
sudo apt-get install xmms-scrobbler
```

That should serve the purpose if you don't mind using a different media player to achieve the same result.[/QUOTE]

Yes, the plug-in adds to your profile, but the site does more. 

The Last.fm Player is required for customized streaming radio stations.  These will also be added to your profile when you play them.

I, too, haven't been able to get the player to work in Linux.  The static binary crashes whenever I try to load a station in Dapper and Breezy and on my desktop and laptop.  I am questioning the quality of the package.

---

### Post by Thorne on 2006-06-08
Humm i installed that plugin for XMMS, and have an account at last.fm but there seems to be some problem with it. It won't store my password for some reason. Got any ideas how to fix it?

---

