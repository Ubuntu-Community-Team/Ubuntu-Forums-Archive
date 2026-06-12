---
title: "Mov Files not playing embeded in Firefox"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by Mudbream on 2005-12-19
Hi,
I've got Kubuntu 5.10 running and have managed to get mov files playing, but only in Mplayer running seperatly from Firefox 1.5. I know this works as I downloaded a mov file this site : [http://www.compfused.com/directlink/1088/](http://www.compfused.com/directlink/1088/) and then opened it in Mplayer and it all worked great!
Apologies if this has been asked before, but I can't seem to find it.
How can I get this to play embeded in the webpage?
At the moment it tells me that the plugin is not installed and I need to find one (which it doesn't know which one).

Could anyone point me in the right direction or give me a RTFM to read!

Thanks!
Mudbream

---

### Post by frodon on 2005-12-19
Try the Media Player Connectivity extention of firefox.
Or the mplayer plugin : [http://ubuntuforums.org/showthread.php?t=75817](http://ubuntuforums.org/showthread.php?t=75817)

---

### Post by Mudbream on 2005-12-19
Thanks. Will give that a try when I get home this evening.

---

### Post by Mudbream on 2005-12-19
Hi,

This didn't work out so well. I got an error on the last step of that How To.


jeremy@mudders:~$ sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
dpkg: regarding mplayerplug-in_3.11-1_i386.deb containing mplayerplug-in:
mozilla-mplayer conflicts with mplayerplug-in
mplayerplug-in (version 3.11-1) is to be installed.
dpkg: error processing mplayerplug-in_3.11-1_i386.deb (--install):
conflicting packages - not installing mplayerplug-in
Errors were encountered while processing:
mplayerplug-in_3.11-1_i386.deb

All the other parts worked great. Any idea what the problem could be?

Thanks,
Mudbream

---

### Post by Rackerz on 2005-12-19
Go into Adept and find the mplayer-mozilla plugin and install that.

---

### Post by Mudbream on 2005-12-20
[QUOTE=Rackerz]Go into Adept and find the mplayer-mozilla plugin and install that.[/QUOTE]

Looks like I already had that installed.
Any other idea's?

Thanks.

---

### Post by Mudbream on 2005-12-20
I just ran that script of Arnieboy's. I had run it before and it all looked like it worked before. 
Ran it again and now I get the embeded Quicktime stuff working!
I saw on one of his threads though that someone else was also getting all - small, medium and large - files on the apple trailers website all opening at the same time.
So thanks for the help guys. Will follow this up on the other thread now.

Cheers!

---

