---
title: "Firestarter and bittorrent"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-16
Just installed firestarter, but i have many torrents going.
apparently these don't mix well together.
 it keeps blocking my torrent requests, and eventually firestarter just closes down. how do i allow these torrents?

---

### Post by Inxsible on 2007-11-16
Firestarter is just a GUI to the iptables (the actual firewall).

Just because Firestarter closes down, it doesnt mean that the firewall is stopping those connections. Firestarter closes down after some time of inactivity.

As for the blocked connections, try and open port 6881-6889 in firestarter in the Policy tab

---

### Post by jordank on 2007-11-16
why does it keep telling me that it blocks port 6881 then?

---

### Post by Inxsible on 2007-11-16
> **jordank said:**
> why does it keep telling me that it blocks port 6881 then?coz you probably havent opened the ports yet

---

### Post by jordank on 2007-11-16
no i havent, nor would i know how.
Havent played around with any ports at all. what would be this procedure?

---

### Post by Inxsible on 2007-11-16
On the Policy tab, make sure you are editing the inbound traffic policy

In the second text area, right click on it and select Add Rule.

Select the name from the drop down list. once you do that, the default port for that service will automatically appear in the Port textbox. Give a comment if you like and click Add. then click Apply Policy

---

### Post by mikeize on 2007-12-10
i'm running utorrent in wine and i have firestarter installed and running.  i have the port(s) that utorrent wants open, open (thru firestarter), and things usually work fine.  but often, utorrent shows that the port is blocked!  i can't figure out why one day, the port is open (i check it at a website), and the next day it is blocked (check same site)!  sometimes, it resolves itself if i restart utorrent, but not always.  what gives?  any ideas?

-mike

---

### Post by D_Murdock on 2007-12-11
I keep getting a blocked connection from BitTorrent in Firestarter when I don't even have BitTorrent open, any thoughts? 

Also I read above that Firestarter closes after inactivity? I presume it's still running in the background even after closing out of the taskbar?

---

### Post by kpkeerthi on 2007-12-11
> **D_Murdock said:**
> I keep getting a blocked connection from BitTorrent in Firestarter when I don't even have BitTorrent open, any thoughts? 

Also I read above that Firestarter closes after inactivity? I presume it's still running in the background even after closing out of the taskbar?

To check if firestarter is running, 
```

sudo /etc/init.d/firestarter status

```

---

