---
title: "Trying out FreeBSD"
date: 2011-07-31
forum: Any Other OS
---

### Post by ratcheer on 2011-07-31
I got a new PC in June, but my old one still works well. So yesterday I decided to try FreeBSD on it. What a trip!
 
I pretty much accepted all the defaults in the installation, doing a whole disk, Standard Installation, with a "User" feature set. The install worked well and got me to a command prompt.
 
Next, I discovered that I had no network connectivity. An hour or so of research and fiddling around led me to do "dhclient skc0". I thought I had that problem solved, but the next time after I restarted, that did not work. Searching through dmesg showed me that now my ethernet interface was named "sk0" instead of "skc0" and the dhclient command did work with the new interface name. I wonder if the interface name will continue to change?
 
Finally, I learned to install Gnome2 from their packages system. I wanted to port, but learning to use the ports looks like an adventure in itself. The install ran all afternoon, but I still didn't get Gnome up. More research showed me that I still need to install and configure some other things for it to actually run.
 
FreeBSD people do all this stuff day-in and day-out? My hat is off to you. I am going to keep at it until I get a usable system, but wow! We Ubuntu users really have it good.
 
Tim

---

### Post by ratcheer on 2011-07-31
Ok, I've got the basic system working, now. Gnome 2 is running and the network interface startup is automated. I can't wait to see what's next!

Tim

---

