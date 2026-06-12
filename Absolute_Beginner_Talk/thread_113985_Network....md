---
title: "Network..."
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by JoeZ on 2006-01-07
Ok... I now have one computer that has Windows XP, and one with Ubuntu.
I have wireless network on one (the one with XP). So now I want to connect to internet thorugh the one with with XP to the one with Ubuntu...
Is this at all possible?

---

### Post by ubuntuuser on 2006-01-07
Well, you could use an SSH client, [http://www.ssh.com/support/downloads/secureshellwks/non-commercial.html]("http://www.ssh.com/support/downloads/secureshellwks/non-commercial.html"). But to connect to the other PC through the internet you'll need the other PC's WAN IP (for a lack of a better word), this being the IP the ubuntu-PC got from your ISP. If your ubuntu-PC ist online all the time this should not be a problem, but in case it is often rebooted, it will most likely get always a different IP, so you'll need to find a way to always get the correct one.

edit:

And you will need to configure iptables (the ubuntu firewall) as well as any hardware firewall you might use to allow SSH connections. For iptables I'd recommend using Firestarter, for any other firewall you might have you need to read the manual (which is of course always a good idea ;) )

---

