---
title: "Stopping or removing Network Manager safely"
date: 2008-01-20
forum: Apple PPC Users
---

### Post by stream303 on 2008-01-20
After installing Gutsy on my late 2004 G4 iBook, I found that Network Manager was sucking up nearly all of my cpu resources.

The wrong way: I just proceeded to remove Network Manager with Synaptic and that cured my problem after manually setting all my network interfaces manually.  That is the WRONG WAY to do it.
[B]
The right way can be found here:[/B]

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

I had to reinstall Network Manager and Gnome Network Manager, and then stopped it and wrote two files as root as directed in the community docs above.

That worked, and is the elegant way to do it should you feel that Network Manager is a problem.

---

