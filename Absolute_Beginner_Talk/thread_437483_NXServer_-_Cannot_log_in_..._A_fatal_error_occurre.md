---
title: "NXServer - Cannot log in ... A fatal error occurred in NX Server"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-08
Trying to get NXServer to work with Ubuntu.  I get the following error.  
Anyone have a fix.

Thanks

Carl


NX> 105 Start session with: --link="adsl" --backingstore="1" --streaming="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="cwmoser" --type="unix-gnome" --geometry="3360x1000" --client="linux" --keyboard="pc105\057us" --screeninfo="3360x1000x24+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.

---

### Post by drdnl on 2007-05-09
My guess? Its the --screeninfo="3360x1000x24+render"

You have a screen res of 3360x1000? Not that its impossible but I doubt it, can't tell you how to fix it though. Try searching on details to change nxserver default settings

---

### Post by cwmoser on 2007-05-09
Thanks.  I followed your recommendation to invest in the time and effort to install ssh and NXServer.  NXServer is definitely worth the effort and superior to VNC.

One issue I had with NXServer is that my main account on my system would not allow me to log in.   I got NXServer to work by adding a new user via nxserver.   With the free NXServer, we can only have two accounts but that is no problem.  

Like you mentioned, NXServer does not take over the desktop but instead creates another user session -- I like that over the way VNC takes control of the existing desktop.

NXServer is a really nice addition for Ubuntu.  Its also a brilliant marketing idea to allow for free 2-user access.  Now that we have experience with NXServer, we might find some commercial applications that will need to purchase the ful version.  Thanks for the recommendation.

Carl

---

