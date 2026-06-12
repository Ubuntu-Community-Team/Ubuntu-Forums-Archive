---
title: "Take control over XP computer?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Mochtroid-X on 2007-05-27
Running Ubuntu 7.04 and wondering if I can use remote desktop or something to that effect to connect and take control over a friend's Windows XP Home Edition computer to help him out with it? I have searched the forums and come up with null to help me, just more confusion... ](*,)

---

### Post by lazyart on 2007-05-27
If your friend installs VNC server on his machine, you can use the Terminal Services Client included in ubuntu.  Just be sure you set the protocol to VNC.

---

### Post by n8bounds on 2007-05-27
VNC is a nice way to go.  Windows users can install tighvnc, ultravnc, or realvnc.  You can open a terminal and say ```
 vncviewer 22.149.91.22 
``` (I made up the IP address, it would be whatever his is.  Of course, thats assuming he has a public IP address.  Routers/switches with NAT enabled complicate things.  VNC uses port 5800 if that helps you configure your friends router.  There IS a terminal server client for linux that can use the MS-RDP I think, but I've never used it.

---

### Post by Mochtroid-X on 2007-05-27
So if he uses that I can use Gnome-RDP to take control of his keyboard and mouse? I just enter his ip address and password into Gnome-RDP?

---

### Post by pentax on 2007-05-27
Use tsclient I use it to log into a XP machine at work, it works using XP's Remote Desktop, so there is nothing needed to install on the remote machine. You can install tsclient with Synaptic.

---

