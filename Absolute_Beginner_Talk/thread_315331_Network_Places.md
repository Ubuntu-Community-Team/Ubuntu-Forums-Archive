---
title: "Network Places"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-09
First an aside--I installed Edgy over Dapper yesterday, and Firefox seemed very slow at loading some pages.  I just installed Swiftfox, and (if anyone is still wondering) it is much faster.

My problem--I got my network going tonight, but at some unknown point in the process, an icon for one of the other network computers got placed on my desktop and in the Places menu.  Any idea how that might have happened?  I certainly didn't do it intentionally--I don't even know how to add or remove items in the Places, except by bookmarking them in Nautilus, but these icons (network folder icons, not those used for computers in the network window) are not in bookmarks--it's between Network Servers and Connect to Server.  It's also in the sidebar under places in the Nautilus windows.  Could someone tell me how to remove it, please?

Thanks,
Buck

P.S.  It's also in the Network window, beside "Windows Network."

---

### Post by faraazs on 2006-12-09
> **Buck2348 said:**
> First an aside--I installed Edgy over Dapper yesterday, and Firefox seemed very slow at loading some pages.  I just installed Swiftfox, and (if anyone is still wondering) it is much faster.

My problem--I got my network going tonight, but at some unknown point in the process, an icon for one of the other network computers got placed on my desktop and in the Places menu.  Any idea how that might have happened?  I certainly didn't do it intentionally--I don't even know how to add or remove items in the Places, except by bookmarking them in Nautilus, but these icons (network folder icons, not those used for computers in the network window) are not in bookmarks--it's between Network Servers and Connect to Server.  It's also in the sidebar under places in the Nautilus windows.  Could someone tell me how to remove it, please?

Thanks,
BuckNetworked folders are treated as mounted volumes. To get rid of it, unmount it.

---

### Post by shanepardue on 2006-12-09
Or you can edit nautilus in the gconf-editor to not show mounted volumes on 
your desktop. Reply if interested.

---

### Post by Buck2348 on 2006-12-09
When I booted up first time today, I had two copies of that network share in the same places.  I unmounted them and rebooted, expecting one to come back again, but it didn't.  Could you explain how it got mounted to begin with?  I can't imagine what I might have done to cause it, and it was only one of several network shares.  (This never happened with Dapper.)  I also have another small problem with the network:  When I click on the Network icon, I get an icon with the name of the network, and the icon is generic, looks like a text file icon.  When I click on that, I get an error message: **Couldn't Display "smb:///<network name>"**  The location is not a folder. Clicking on the icon some more changes it to the network icon and it will open.  Same thing happens with the individual machines on the network.  I googled this some and came up empty.

Thank you both for your replies and any more help you can give me.

Regards,
Buck

---

