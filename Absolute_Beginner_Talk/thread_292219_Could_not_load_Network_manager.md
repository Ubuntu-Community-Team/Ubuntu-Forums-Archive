---
title: "Could not load Network manager"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Duwady on 2006-11-03
I tried installing network-manager-gnome, because I have to install WPA-wireless,  but I got the following message.

"Network-Manager-Gnome' is not available in any software Channel. The application might not support your system architecture."

The Dapper CD was in the CD-drive.

And I am stumped ... 

Any other things that I need to do?  Any help on installing Network Manager, or some other way to get WPA would be really really appreciated...

Thanks.

---

### Post by rdd on 2006-11-03
Don't really know about that error but you could try removing the CD from your apt configuration to force it to download it from the net. Do that in your Synaptic under 'Settings' -> 'Repositories' and then click 'Reload'.

Other question about the architecture: Are you running on AMD64? 


rdd

---

### Post by Duwady on 2006-11-03
> **rdd said:**
> Don't really know about that error but you could try removing the CD from your apt configuration to force it to download it from the net. Do that in your Synaptic under 'Settings' -> 'Repositories' and then click 'Reload'.

Other question about the architecture: Are you running on AMD64? 


rdd

I will try to do what you have suggested, and will come back with what happens.

I am using P4 3.2GHz, not AMD64

Thank you.

---

### Post by jimrz on 2006-11-03
> **Duwady said:**
> I tried installing network-manager-gnome, because I have to install WPA-wireless,  but I got the following message.

"Network-Manager-Gnome' is not available in any software Channel. The application might not support your system architecture."

The Dapper CD was in the CD-drive.

And I am stumped ... 

Any other things that I need to do?  Any help on installing Network Manager, or some other way to get WPA would be really really appreciated...

Thanks.

are you not on-line? which dapper cd do you have?

the "alternate cd" has both .debs on it (but the "live cd" does not) just pop it in your drive, then go to pool > main > n > network-manager. copy the .debs to your desktop and install by double clicking

OR it could be as simple as it is network-manager network-manager-gnome NOT Network-Manager-Gnome

---

### Post by koujaku on 2007-09-09
yeah, man! i got the same thing everytime i tried to install anything from add/remove.

"the application might not support your system architecture"

it all started when i installed ubuntu. via live cd i didnt get that.

any help?

---

### Post by koujaku on 2007-09-19
problem solved. i just updated ubuntu and the problem is gone.

---

