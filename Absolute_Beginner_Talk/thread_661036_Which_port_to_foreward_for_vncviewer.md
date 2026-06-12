---
title: "Which port to foreward for vncviewer?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Hospadar on 2008-01-07
My machine is behind a router and i'm assuming I'll need to foreward a port to my machine to use vncviewer (for remote desktop) but I'm not really sure which port I need to foreward.  From a few things I've read, it looks like I could choose which port that is, but I don't know where I'd do that.

Also would I need to open up that port in iptables? (I know how to do that, I just don't know if it's necesary)

Thanks!

---

### Post by stalker145 on 2008-01-07
> **Hospadar said:**
> My machine is behind a router and i'm assuming I'll need to foreward a port to my machine to use vncviewer (for remote desktop) but I'm not really sure which port I need to foreward.  From a few things I've read, it looks like I could choose which port that is, but I don't know where I'd do that.

Also would I need to open up that port in iptables? (I know how to do that, I just don't know if it's necesary)

Thanks!

1. The port to forward for VNC is 5900

2. I don't know how to change the port to something less likely to be probed.

3. Why not use something (like FreeNX, Hamachi, NoMachine, or simple SSH) that is more secure?

4. Not sure about iptables. I use my router as the "firewall"

---

### Post by Hospadar on 2008-01-07
thanks a bunch, the only reason I'd want to use a remote viewer instead of ssh is so I can start graphical things and not kill them when i log out. (like big video transcoding jobs and the like)

---

