---
title: "FireWire don't work"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by AchimRS on 2007-02-01
Hi,
I have problems accessing a camera connected via Firewire. When I insert the FireWire card,"dmesg" shows the following:

ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[00e0263d00026d1b]
ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[00e0263d00026d1b]
ieee1394: Error parsing configrom for node 0-01:1023
ieee1394: Node suspended: ID:BUS[0-00:1023] GUID[00004c0100000264]

When I connect the switched-off camera, no message appears ;-)
When I switch on the camera the following message appear:

ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00e0263d00026d1b]
ieee1394: Node changed: 0-00:1023 -> 0-01:1023

From my point of view, everything looks fine, but I cant access the files on the camer e.g.via /media 

Any hint what is missed here???

Thanks
   Achim

---

