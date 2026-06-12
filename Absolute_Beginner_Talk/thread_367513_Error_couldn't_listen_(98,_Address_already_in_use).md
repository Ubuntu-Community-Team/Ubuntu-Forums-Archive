---
title: "Error couldn't listen: (98, Address already in use)"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by lastredoubt on 2007-02-22
Hi again,

I'm not exactly sure how to even classify this problem, nor even relate what software is screwing up.  I don't think it is even Ubuntu specific.  I can really only relate the circumstances and hope someone out there knows what it's all about and how to help me.  

I have been opening torrent files by clicking on them and electing to open with ktorrent (in gnome) rather than save as.  When I do so, the download of the torrent file to a tmp works fine but then when it attempts to open it gives me an odd error message in an untitled window:

Error  Couldn't listen - (98,' Address already in use')

I'm not exactly sure what this is telling me, so I'm not sure how to fix it.  The torrent files themselves work fine when opened from ktorrent, but the so-called automatic process from firefox isn't happening.  Any help?

Thanks,
Daniel

---

### Post by ScottFW on 2007-02-22
ktorrent in gnome? Why not use the gnome bittorrent?

In any case, that error probably arises because the port the program is trying to use for the torrent is already in use by something else. This same error will pop up in gnome's bittorrent if you try to have multiple torrents going at once, and it's because the minimum port and maximum port values are set to the same number, so only one port gets used. To fix it, type gconf-editor in a terminal window, navigate to "apps" then find the offending app that's giving you the error message (ktorrent?), then click on "settings" and change the max_port number to something higher.

Also see this thread.
[http://www.ubuntuforums.org/showthread.php?t=343229](http://www.ubuntuforums.org/showthread.php?t=343229)

---

