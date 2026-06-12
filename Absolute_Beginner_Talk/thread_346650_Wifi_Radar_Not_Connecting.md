---
title: "Wifi Radar Not Connecting"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Hishgraphics on 2007-01-26
Hi all,

I'm currently browsing in a mall, but I'm on WinXP connected to the wifi router here because I can't get WiFi Radar on the Ubuntu on this very laptop to connect even though it can detect the signal of the routers.

When I hit the connect button, it tells me it's trying to acquire an IP address but in the end it's still "Not Connected".

Am I missing something in the equation? Help!

---

### Post by citizenofnowhere on 2007-01-26
That happens sometimes to me too and I'm not entirely sure why. At home I reset the router but on a shared open connection that may not be possible.

What you could try next time around (I assume you're not still at the mall). 

In System->Administration->Networking, uncheck the Wireless box. Look at the Properties for that connection - try to set the network ID and everything for your location manually. Check that DHCP is enabled (this allows the router to give you an IP address). Then enable Wireless again and let it connect without wifi-radar. Most of the time that does the trick (especially if it's an open network).

---

### Post by Hishgraphics on 2007-01-26
Thanks, I'll try that the first chance I get.

---

### Post by mexlinux on 2007-01-26
wifi-radar never worked for me.
try wlassistant

---

### Post by ComplexNumber on 2007-01-26
> **Hishgraphics said:**
> Hi all,

I'm currently browsing in a mall, but I'm on WinXP connected to the wifi router here because I can't get WiFi Radar on the Ubuntu on this very laptop to connect even though it can detect the signal of the routers.

When I hit the connect button, it tells me it's trying to acquire an IP address but in the end it's still "Not Connected".

Am I missing something in the equation? Help!
just a haunch, but install network manager too (if you haven't already). i managed to get wireless working after a while. posted the steps somewhere in the network forum here.
can i assume that you've done all the usual things such as installed ndiswrapper, installed the windows drivers, etc?

---

