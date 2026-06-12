---
title: "Help with VPN connection in Backtrack5 R2 KDE"
date: 2012-06-25
forum: Any Other OS
---

### Post by helpmonkey on 2012-06-25
I typically use swissvpn.net for my VPN provider. I was while testing BT5 Gnome able to connect to it with no problem. I tested out BT5 kde and instantly fell in love with it. I've tried to set up the VPN using all possible network managers and other tools that handle VPN accounts but not a single one of them have worked. When I boot into the OS I'm automatically connected to the internet yet in the lower right there is the little icon that looks like an empty ethernet jack that says no connections are managed or no connections are set up, not even my ethernet connection registers in that window. Using if I remember right (I'm at work now on crappy Windows 7) It was the KDE Network manager. I was able to hit the VPN tab and set up the basics as the swissvpn.net site had suggested using that app, but it will show it as SwissVPN (the name I gave it) and when I go to click on it to connect it will not do anything. I have tried going about it through the OpenVPN method they offer on the support page, but the same still is the problem. When I open it up to edit the connection after signing in with I think it's KDE Wallet, everything is set how I left it, but under the ethernet connection and the VPN connection is has it's title for the connection but has 'never' as being used. I recently encrypted my entire HDD, I'm sure that has nothing to do with it, but I am not seeing any results. Nor have I found (yet) anything on the Backtrack 5 forums regaurding the issue. I have found that responses there are few and far between it is why I opted to try on this forum to see if I could possible find some answers. The other thing I run into as well is when trying to install some of the other network related tools, I get an error message once the download has finished yet it shows as though it is installed. Thank you ahead of time for any help. I would really like to get this situation hammered out ASAP, but I do understand others lives are busy and I'm the one asking for help. So it's not my time used in helping me.
Thank you again for any help.

---

### Post by nothingspecial on 2012-06-25
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by helpmonkey on 2012-06-26
I managed to solve the problem by using the OpenVPN method located on the swissvpn.net page.  Although I did the apt-get update before restarting the network, also once I was into Open VPN I unchecked connect automatically, and I had to uncheck Available to all user.  Having those checked gave me errors of secrets or the likes or would connect for 3 seconds and fail.  Hope this might help someone.  I feel retarded asking in the first place, cause most times I figure it out before I get a reply.  lol.

---

