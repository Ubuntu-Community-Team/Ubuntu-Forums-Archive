---
title: "how do I log on to a remote desktop"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Jonas_Henricsson on 2006-10-30
Hi!

I want to log on to a remote desktop from my ubuntu system. What do I use in Ubuntu for this purpose? 

I searched for info, but it seems like doing what I want to do is so obvious to everyone that everyone is only asking about how they can make their own system available through remote desktop.

Thanks for any help!

/Jonas

---

### Post by tronica on 2006-10-30
I use tsclient, go to Applications -> Internet -> Terminal Server Client. It can do RDP, and vnc.

---

### Post by fguilhon on 2006-10-30
It really depends on the OS (type of remote server listening on) the remote machine has. You can use VNC on both Windows and Linux. 
RDP is Windows protocol... and on Linux you can use XDMCP.
For starters, I think VNC is nice.

---

