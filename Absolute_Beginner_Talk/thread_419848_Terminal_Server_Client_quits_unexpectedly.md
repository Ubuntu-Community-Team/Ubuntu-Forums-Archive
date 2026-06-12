---
title: "Terminal Server Client quits unexpectedly"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by infernon on 2007-04-23
While using the terminal server client, I am disconnected from the server after right-clicking to bring up a menu or clicking on the Start Menu.  In fact, it appears that just about any menu that I click on causes the client to disconnect/quit immediately after I attempt to click off of it.  There are no error messages, the program simply quits.  This also happens frequently immediately after I submit a user name and a password when attempting to log on.  I should mention that the same thing happens with a Windows 2003 server and an XP Pro machine.

I am using RDPv5, sounds are set to not play and I've manipulated the performance settings just about every possible way to rule out that being the source of the problem.

---

### Post by MikeEvans on 2007-04-23
Try reinstalling or upgrading the RDP server on the host.  If its XP you might want to try RDPv6 if you haven't already.  You can connect to it with the RDPv5 client.  If that doesn't do it you might want to try installing a VNC server on the host.  I use UltraVNC on my Windows hosts.  If VNC works then you can eliminate most network issues from the list of suspects.  You could then do a complete removal of the RDP server on the host including registry entries and application data then reinstalling.  If VNC behaves the same way you should examine the network route.

---

### Post by jasonmtroos on 2007-04-24
I'm experiencing exactly the same problem as infernon: anytime I right-click on something, the session exists (but the RDP client app remains open). 

MikeEvans suggests reinstalling the software on the host. In my case, this is not an option, as I do not have administrative privileges on the server. Furthermore, the server has remained unchanged whereas the client machine has been updated from Edgy Eft to Feisty Fawn. Sessions prior to the upgrade worked well; since the upgrade none have worked.

---

